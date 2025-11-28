<script setup>
	defineProps({
		show: {
			type: Boolean,
			required: true,
		},
		title: {
			type: String,
			default: "¿Estás seguro?",
		},
		message: {
			type: String,
			default: "Esta acción no se puede deshacer.",
		},
		confirmText: {
			type: String,
			default: "Confirmar",
		},
		cancelText: {
			type: String,
			default: "Cancelar",
		},
		confirmButtonClass: {
			type: String,
			default:
				"flex-1 bg-linear-to-r from-rose-500 to-red-500 hover:from-rose-600 hover:to-red-600 text-white px-4 py-2 rounded-xl hover:scale-105 transition-all duration-200",
		},
		borderColor: {
			type: String,
			default: "border-red-500",
		},
	});
	const emit = defineEmits(["close", "confirm"]);
</script>
<template>
	<!-- Backdrop -->
	<div
		class="fixed inset-0 bg-black/50 backdrop-blur-sm z-50 flex items-center justify-center p-4"
		@click.self="emit('close')"
	>
		<!-- Modal Container -->
		<div
			:class="[
				'bg-white rounded-2xl shadow-2xl p-8 max-w-md w-full transform transition-all duration-300 scale-100 border-b-4',
				borderColor,
			]"
		>
			<!-- Modal Content -->
			<div class="flex items-center justify-center flex-col gap-6">
				<div class="text-center">
					<h3
						v-if="title"
						class="text-xl font-bold text-gray-800 mb-2"
					>
						{{ title }}
					</h3>
					<p class="text-gray-600">
						{{ message }}
					</p>
				</div>
				<div class="flex gap-3 w-full">
					<button
						class="flex-1 bg-linear-to-r from-gray-500 to-slate-500 hover:from-gray-600 hover:to-slate-600 text-white px-4 py-2 rounded-xl hover:scale-105 transition-all duration-200"
						@click="emit('close')"
					>
						{{ cancelText }}
					</button>
					<button
						:class="confirmButtonClass"
						@click="emit('confirm')"
					>
						{{ confirmText }}
					</button>
				</div>
			</div>
		</div>
	</div>
</template>
