<script setup>
const props = defineProps({
	text: String,
});
</script>

<template>
    <div class="detail">
    <details>
        {{ props.text }}
        <summary></summary>
    </details>
    </div>
</template>

<style scoped>
.detail {
	width: 500px;
	overflow-wrap: anywhere;
	word-break: break-all;
}
details {
	padding: 0 13%;
	font-size: .8em;
	line-height: 1.4em;
	text-align: left;
	& > summary::after {
		content: "<|>";
	}
	&[open] > summary::after {
		content: "</>";
	}
}
summary {
	font-size: 1rem;
	text-align: center;
	list-style: none;
	line-height: 2em;
}

summary {
	cursor: pointer;
}

@media (width <= 768px) {
	.detail {
		width: 250px;
	}
}
</style>