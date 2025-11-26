<script setup>
	defineProps({
		type: {
			type: String,
			validator: (value) =>
				["info", "success", "warning", "error"].includes(value),
		},
	});

	const typeClasses = {
		info: "bg-blue-100 border-blue-300 text-blue-800",
		success: "bg-green-100 border-green-300 text-green-800",
		warning: "bg-yellow-100 border-yellow-300 text-yellow-800",
		error: "bg-red-100 border-red-300 text-red-800",
	};
</script>

<template>
	<!-- Plantilla para mensajes -->
	<!-- Alinear a la derecha -->
	<div class="fixed top-4 right-4 w-full max-w-md px-4">
		<div
			:class="`p-4 rounded-lg border-l-4 ${typeClasses[type]}`"
		>
			<slot></slot>
		</div>
	</div>
</template>
