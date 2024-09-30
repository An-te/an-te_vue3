<script setup>
const props = defineProps({
	img: String,
});
</script>

<template>
    <img :src="props.img"/>
</template>

<style scoped>
    img {
        height: 400px;
        width: 100%;
        display: block;
        object-fit: cover;
    }
</style>
