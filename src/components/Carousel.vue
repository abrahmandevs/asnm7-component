<script setup>
	import { ref, onMounted, onBeforeUnmount, nextTick } from "vue"
	const props = defineProps(["id", "images"])

	let carousel = null

	onMounted(() => {
		const carouselId = document.getElementById(props.id)
		carousel = new Flickity(carouselId, {})
	})
	onBeforeUnmount(() => {
		carousel.destroy()
		// nextTick(() => {
		//     carousel.destroy()
		// })
	})
	console.log(props.id)
</script>

<template>
	<h2 class="">Task-1 Carousel</h2>
	<div class="mx-auto items" :id="props.id">
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

