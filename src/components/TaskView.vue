<script setup>
	// Componentes
	import TaskCard from "@/components/TaskCard.vue";

	// Props
	defineProps({
		tasksList: {
			type: Array,
			required: true
		}
	});

</script>

<template>
	<section class="flex flex-col justify-center items-center gap-4 my-8 mx-4">
		<h3 class="text-4xl font-semibold mb-4 text-gray-800">
			Lista de Tareas
		</h3>
		<TaskCard v-for="task in tasksList" :key="task.id" :task="task" />
	</section>
</template>
