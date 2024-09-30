<script setup>
import { ref, onMounted } from "vue";
import p5 from "p5";
import Details from "@/components/Details.vue";

const props = defineProps({
	item: Object,
});

function F(f, id) {
	onMounted(() => {
		const p = new p5(f, document.getElementById(id));
		setTimeout(() => {
			p.canvas.addEventListener("click", () =>
				p.isLooping() === true ? p.noLoop() : p.loop(),
			);
			const observer = new IntersectionObserver((entries, observer) => {
				const entry = entries[0];
				// for (const entry of entries) {
					if (entry.isIntersecting) {
						p.loop();
						entry.target.classList.add("anim");
					} else {
						p.noLoop();
						entry.target.classList.remove("anim");
					}
				// }
			});
			observer.observe(p.canvas);
		}, 300);
	});
}
F(props.item.func, props.item.id);
</script>

<template>
    <Details :text="props.item.text" />
    <p>{{ props.item.t }}</p>
</template>