<script setup>
	import { ref, onMounted } from "vue";
	
	// Importación de datos de tareas temporales
	import { tasks } from "@/data/tasks.js";

	// Componentes
	import Header from "@/components/Header.vue";
	import Hero from "@/components/Hero.vue";
	import TaskView from "@/components/TaskView.vue";
	import FormTask from "@/components/FormTask.vue";

	// Variable reactiva para almacenar las tareas
	const tasksList = ref([]);
	// Variables para el formulario de nueva tarea
	const title = ref("");
	const priority = ref("baja");
	const estimatedPomodoros = ref("");
	const completed = ref(false);


	// Simulación de carga de datos
	onMounted(() => {
		tasksList.value = tasks;
	})

	// Función para recibir la nueva tarea del formulario
	const handleNewTask = (taskData) => {
		tasksList.value.push({
			id: Math.random().toString(36).substr(2, 9),
			title: taskData.title,
			priority: taskData.priority,
			estimatedPomodoros: taskData.estimatedPomodoros,
			completed: taskData.completed,
		});
		// console.log('Tarea agregada. Lista actualizada:', tasksList.value);
	};
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
		/>
		<!-- Task View Section (Temporal hasta que aplique las rutas)-->
		<TaskView :tasksList="tasksList" />
	</div>
</template>

<style scoped></style>
