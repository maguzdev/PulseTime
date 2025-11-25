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

	// Simulación de carga de datos
	onMounted(() => {
		tasksList.value = tasks;
	})
</script>

<template>
	<div>
		<!-- Header -->
		<Header />
		<!-- Hero Section -->
		<Hero />
		<!-- Form Task Section (Temporal hasta que aplique las rutas)-->
		<FormTask />
		<!-- Task View Section (Temporal hasta que aplique las rutas)-->
		<TaskView :tasksList="tasksList" />
	</div>
</template>

<style scoped></style>
