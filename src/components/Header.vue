<script setup>
	import LogoBrand from "@/components/ui/LogoBrand.vue";
	import Navigation from "@/components/Navigation.vue";
</script>

<template>
	<header
		class="bg-white flex bg-linear-to-r from-violet-400 via-violet-400 to-indigo-400 to-100% items-center border-b-8 border-violet-200 py-4"
	>
		<div
			class="flex flex-col md:flex-row justify-between items-center w-full px-6 gap-4"
		>
			<!-- Logo -->
			<a href="/"><LogoBrand /></a>
			<!-- Navigation -->
			<Navigation />
		</div>
	</header>
</template>
