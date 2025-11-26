<script setup>
	import { ref, onMounted, watch, provide } from "vue";

	// Importación de datos de tareas temporales
	import { tasks } from "@/data/tasks.js";

	// Componentes
	import Header from "@/components/Header.vue";
	import Hero from "@/components/Hero.vue";
	import TaskView from "@/components/TaskView.vue";
	import FormTask from "@/components/FormTask.vue";
	import Message from "@/components/ui/Message.vue";

	// Variable reactiva para almacenar las tareas
	const tasksList = ref([]);
	// Variables para el formulario de nueva tarea
	const title = ref("");
	const priority = ref("");
	const estimatedPomodoros = ref("");
	const completed = ref(false);
	// Variables para el mensaje
	const showMessage = ref(false);
	const messageType = ref("");
	const messageText = ref("");

	// Watcher para guardar tareas en localStorage cuando cambien
	watch(
		tasksList,
		() => {
			saveTasksToLocalStorage();
		},
		{ deep: true }
	);

	// Guardar tareas en localStorage
	const saveTasksToLocalStorage = () => {
		localStorage.setItem("tasks", JSON.stringify(tasksList.value));
	};

	// Simulación de carga de datos
	onMounted(() => {
		tasksList.value = tasks;
		// Cargar tareas desde localStorage si existen
		const savedTasks = localStorage.getItem("tasks");
		if (savedTasks) {
			tasksList.value = JSON.parse(savedTasks);
		}
	});

	// Función para recibir la nueva tarea del formulario
	const handleNewTask = (taskData) => {
		tasksList.value.push({
			id: Math.random().toString(36).substr(2, 9),
			title: taskData.title,
			priority: taskData.priority || "baja",
			estimatedPomodoros: taskData.estimatedPomodoros,
			completed: taskData.completed,
		});
		handleSuccessMessage("Tarea agregada correctamente.");
	};

	const handleSuccessMessage = (successMessage) => {
		messageType.value = "success";
		messageText.value = successMessage;
		showMessage.value = true;
		setTimeout(() => {
			clearMessage();
		}, 3000);
	};

	const handleErrorMessage = (errorMessage) => {
		messageType.value = "error";
		messageText.value = errorMessage;
		showMessage.value = true;
		setTimeout(() => {
			clearMessage();
		}, 3000);
	};

	const deleteTask = (taskId) => {
		// console.log("Eliminar tarea con ID:", taskId);
		tasksList.value = tasksList.value.filter((task) => task.id !== taskId);
		handleSuccessMessage("Tarea eliminada correctamente.");
	};

	const toggleTaskCompletion = (taskId) => {
		const task = tasksList.value.find((task) => task.id === taskId);
		if (task) {
			task.completed = !task.completed;
		}
	};

	const clearMessage = () => {
		messageText.value = "";
		messageType.value = "";
		showMessage.value = false;
	};

	// Proveer la función deleteTask a todos los componentes descendientes
	provide("deleteTask", deleteTask);
	provide("toggleTaskCompletion", toggleTaskCompletion);
</script>

<template>
	<div class="mb-16">
		<!-- Header -->
		<Header />
		<!-- Hero Section -->
		<Hero />
		<!-- Form Task Section (Temporal hasta que aplique las rutas)-->
		<FormTask
			v-model:title="title"
			v-model:priority="priority"
			v-model:estimatedPomodoros="estimatedPomodoros"
			v-model:completed="completed"
			@submit="handleNewTask"
			@error="handleErrorMessage"
		/>
		<!-- Message Component -->
		<Message v-if="showMessage" :type="messageType">
			{{ messageText }}
		</Message>
		<!-- Task View Section (Temporal hasta que aplique las rutas)-->
		<TaskView :tasksList="tasksList" />
	</div>
</template>

<style scoped></style>
