<script setup>
	// Props para v-model
	const props = defineProps({
		title: String,
		priority: String,
		estimatedPomodoros: String,
		completed: Boolean,
	});

	// Emits para v-model
	const emit = defineEmits([
		"update:title",
		"update:priority",
		"update:estimatedPomodoros",
		"update:completed",
		"submit",
		"error",
	]);
	// Función para manejar el envío del formulario
	const handleSubmit = () => {
		if (props.title) {
			emit("submit", {
				title: props.title,
				priority: props.priority,
				estimatedPomodoros: props.estimatedPomodoros,
			});
			// Limpiar los campos después de enviar
			emit("update:title", "");
			emit("update:priority", "");
			emit("update:estimatedPomodoros", "");
		} else {
			emit("error", "El título de la tarea es obligatorio.");
		}
	};
</script>

<template>
	<section class="mt-8 p-6 bg-white rounded-2xl shadow-md max-w-2xl mx-auto">
		<h2 class="text-2xl font-semibold mb-6 text-gray-800 text-center">
			✨ Agregar Nueva Tarea
		</h2>
		<form
			@submit.prevent="handleSubmit"
			class="flex flex-col gap-4 max-w-md mx-auto"
		>
			<!-- Title -->
			<input
				type="text"
				:value="title"
				@input="emit('update:title', $event.target.value)"
				placeholder="Título de la tarea"
				class="bg-white border border-violet-500/30 hover:border-violet-500/50 focus:border-violet-400 focus:ring-2 focus:ring-violet-500/30 p-4 rounded-xl text-gray-800 placeholder-gray-400 transition-all duration-200 outline-none"
			/>

			<!-- Priority -->
			<select
				:value="priority"
				@change="emit('update:priority', $event.target.value)"
				class="bg-white border border-violet-500/30 hover:border-violet-500/50 focus:border-violet-400 focus:ring-2 focus:ring-violet-500/30 p-4 rounded-xl text-gray-800 transition-all duration-200 outline-none"
			>
				<option value="" disabled selected>Selecciona prioridad</option>
				<option value="baja">Baja</option>
				<option value="media">Media</option>
				<option value="alta">Alta</option>
			</select>

			<!-- Estimated Pomodoros -->
			<input
				type="number"
				min="1"
				:value="estimatedPomodoros"
				@input="emit('update:estimatedPomodoros', $event.target.value)"
				placeholder="Pomodoros estimados"
				class="bg-white border border-violet-500/30 hover:border-violet-500/50 focus:border-violet-400 focus:ring-2 focus:ring-violet-500/30 p-4 rounded-xl text-gray-800 placeholder-gray-400 transition-all duration-200 outline-none"
			/>

			<!-- Submit Button -->
			<button
				class="bg-linear-to-r from-violet-600 to-purple-600 hover:from-violet-700 hover:to-purple-700 text-white p-4 rounded-xl transition-all duration-200 font-semibold shadow-lg hover:shadow-violet-500/30 hover:scale-105 active:scale-95 transform cursor-pointer"
			>
				<span class="flex items-center justify-center gap-2">
					<svg
						class="w-5 h-5"
						fill="currentColor"
						viewBox="0 0 20 20"
					>
						<path
							fill-rule="evenodd"
							d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z"
							clip-rule="evenodd"
						/>
					</svg>
					<i class="pi pi-plus"></i>
					Agregar Tarea
				</span>
			</button>
		</form>
	</section>
</template>
