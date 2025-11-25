<template>
	<section class="mt-8 p-6 bg-white rounded-2xl shadow-md max-w-2xl mx-auto">
		<h2 class="text-2xl font-semibold mb-6 text-gray-800 text-center">
			✨ Agregar Nueva Tarea
		</h2>
		<form @submit.prevent="" class="flex flex-col gap-4 max-w-md mx-auto">
			<input
				type="text"
				placeholder="Título de la tarea"
				class="bg-white border border-violet-500/30 hover:border-violet-500/50 focus:border-violet-400 focus:ring-2 focus:ring-violet-500/30 p-4 rounded-xl text-gray-800 placeholder-gray-400 transition-all duration-200 outline-none"
			/>
			<select
				class="bg-white border border-violet-500/30 hover:border-violet-500/50 focus:border-violet-400 focus:ring-2 focus:ring-violet-500/30 p-4 rounded-xl text-gray-800 transition-all duration-200 outline-none"
			>
				<option value="" disabled selected>Seleccionar proyecto</option>
				<option value="proyecto1">Marketing</option>
				<option value="proyecto2">Desarrollo</option>
				<option value="proyecto3">Ventas</option>
				<option value="proyecto4">PulseTime</option>
			</select>
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
