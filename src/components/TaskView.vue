<script setup>
	// Importación de Vue
	import { ref } from "vue";

	// Componentes
	import TaskCard from "@/components/TaskCard.vue";

	// Props
	defineProps({
		pendingTasks: {
			type: Array,
			required: true,
		},
		completedTasks: {
			type: Array,
			required: true,
		},
	});

	const viewCompletedTasks = ref(false);

	const toggleView = () => {
		viewCompletedTasks.value = !viewCompletedTasks.value;
	};
</script>

<template>
	<section class="flex flex-col justify-center items-center gap-4 my-8 mx-4">
		<h3 class="text-4xl font-semibold mb-4 text-gray-800">
			Lista de Tareas
		</h3>
		<div class="flex items-center gap-3">
			<!-- Switch para alternar entre tareas pendientes y completadas -->
			<span class="text-gray-700 font-medium">Pendientes</span>
			<label class="relative inline-flex items-center cursor-pointer">
				<input
					type="checkbox"
					@click="toggleView"
					class="sr-only peer"
				/>
				<div
					class="w-14 h-7 bg-gray-300 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-violet-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-0.5 after:left-1 after:bg-white after:border-gray-300 after:border after:rounded-full after:h-6 after:w-6 after:transition-all peer-checked:bg-violet-500"
				></div>
			</label>
			<span class="text-gray-700 font-medium">Completadas</span>
		</div>
		<p v-if="pendingTasks.length === 0">No hay tareas disponibles.</p>
		<TaskCard
			v-if="viewCompletedTasks"
			v-for="task in completedTasks"
			:key="task.id"
			:task="task"
		/>
		<TaskCard
			v-if="!viewCompletedTasks"
			v-for="task in pendingTasks"
			:key="task.id"
			:task="task"
		/>
	</section>
</template>
