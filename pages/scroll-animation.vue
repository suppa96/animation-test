<template>
  <div class="py-96">
    Ciao Ciao
    <div class="box h-10 w-10 bg-red-500 my-96" ref="boxA"></div>
    <div class="box h-10 w-10 bg-green-500 my-96" ref="boxB"></div>
    <div class="box h-10 w-10 bg-blue-500 my-96" ref="boxC"></div>
  </div>
</template>

<script setup lang="ts">
import { gsap } from "gsap";
import { VNodeRef } from "nuxt/dist/app/compat/capi";

definePageMeta({
  title: "Scroll Animations",
  layout: "long-scroll",
});

const boxA = ref();
const boxB = ref();
const boxC: VNodeRef = ref();

let tweenA: any;

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger);
  tweenA = gsap.to(boxC.value, {
    x: 400,
    scrollTrigger: boxC.value,
    rotation: 360,
    duration: 3,
  });
});

onUnmounted(() => {
  tweenA.revert();
});
</script>

<style scoped></style>
