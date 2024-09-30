<script setup>
import { ref, onMounted } from "vue";
import sketches from "../assets/sketch/sketch.js";
import Img from "@/components/Img.vue";
import P5Sketch from "@/components/P5Sketch.vue";
import p5 from "p5";

p5.prototype.shuffle(sketches, true);
sketches.map((e, i) => {
	if (e.type === "p5js") e.id = `P5Sketch${i}`;
});
const items = ref(sketches);
</script>

<template>
    <div class="parent" id="parent">
      <template v-for="item in items">
        <div v-if="item.type === 'p5js'" class="child" :id="item.id">
          <P5Sketch :item="item" />
        </div>
        <div v-else-if="item.type === 'img'" class="child">
          <Img :img="item.img" />
        </div>
    </template>
    </div>
</template>

<style scoped>
  .parent {
    display: flex;
    flex-wrap: wrap;
  }
  .child {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    overflow: hidden;
  }
  .parent > div {
	margin: 2%;
	padding: 24px 24px 29px 24px;
}

.child > span {
	font-size: clamp(1rem, 0.273rem + 3.64vw, 3rem);
	display: flex;
	align-items: center;
	height: 100%;
	overflow-wrap: anywhere;
	word-break: break-all;
}

</style>