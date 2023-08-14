<script setup>
	import { ref, onMounted, onBeforeUnmount, nextTick } from "vue"
	defineProps(["id", "images"])

	let carousel = null

	onMounted(() => {
		carousel = new Flickity("#carousel", {})
	})
	onBeforeUnmount(() => {
		carousel.destroy()
	})
</script>

<template>
	<div class="mx-auto items" id="carousel">
		<div :style="`background-image:url(${image.image})`" class="item bg-cover bg-[#ccc]" v-for="(image, index) in images" :key="index">
			{{ image.image_title }}
		</div>
	</div>
</template>

<style scoped>
	.items {
		width: 600px;
		height: 400px;
	}
	.item {
		width: 600px;
		height: 400px;
	}
</style>

