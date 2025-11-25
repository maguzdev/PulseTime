<script setup>
	defineProps({
		task: {
			type: Object,
			required: true,
		},
	});
</script>

<template>
	<div
		class="flex items-center bg-white rounded-xl shadow-lg p-6 max-w-md md:max-w-2xl w-full md:mx-auto mx-4 space-x-3 flex-1 hover:-translate-y-1 hover:scale-[1.02] transition-all duration-300 ease-in-out hover:shadow-1xl hover:shadow-violet-500/20 hover:border-violet-500/50"
	>
		<!-- Botón para marcar como completada -->
		<button
			:class="[
				'w-6 h-6 rounded-full border-2 flex items-center justify-center transition-all duration-200 hover:scale-110 cursor-pointer',
				task.completed
					? 'bg-violet-500 border-violet-500 text-white shadow-lg shadow-violet-500/30'
					: 'border-violet-400/50 hover:border-violet-400 text-violet-300 hover:bg-violet-500/10',
			]"
			:title="
				task.completed
					? 'Marcar como pendiente'
					: 'Marcar como completada'
			"
		>
			<span v-if="task.completed" class="text-xs font-bold">✓</span>
		</button>

        <!-- Nombre de la tarea -->
        <div class="flex-1">
            <p :class="`text-lg ${task.completed ? 'line-through text-gray-400' : ''}`">{{ task.title }}</p>
        </div>
        
		<!-- Botones de acción -->
			<div class="flex items-center space-x-3">
				<!-- Botón Play/Pomodoro -->
				<button
					:disabled="task.completed"
					class="bg-linear-to-r from-violet-600 to-purple-600 hover:from-violet-700 hover:to-purple-700 disabled:from-gray-600 disabled:to-gray-700 disabled:hover:scale-100 text-white p-2.5 rounded-xl transition-all duration-200 flex items-center justify-center shadow-lg hover:shadow-violet-500/30 hover:scale-105 cursor-pointer disabled:cursor-not-allowed"
					:title="
						task.completed
							? 'No se puede iniciar Pomodoro en tarea completada'
							: 'Iniciar Pomodoro'
					"
				>
					<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
						<path
							d="M6.3 2.841A1.5 1.5 0 004 4.11V15.89a1.5 1.5 0 002.3 1.269l9.344-5.89a1.5 1.5 0 000-2.538L6.3 2.84z"
						/>
					</svg>
				</button>

				<!-- Botón eliminar -->
				<button
					class="bg-linear-to-r from-red-500 to-pink-500 hover:from-red-600 hover:to-pink-600 text-white p-2.5 rounded-xl transition-all duration-200 flex items-center justify-center shadow-lg hover:shadow-red-500/30 hover:scale-105 cursor-pointer"
					title="Eliminar tarea"
				>
					<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
						<path
							fill-rule="evenodd"
							d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z"
							clip-rule="evenodd"
						/>
					</svg>
				</button>
			</div>
	</div>
</template>

<style lang="scss" scoped></style>
