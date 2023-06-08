<template>
  <div>
    <p>Animation starts on mounted</p>
    <div class="h-10 w-10 bg-red-500" ref="boxA"></div>
    <button class="button-default-style" @click="startFromEnd()">
      Restart Animation from End
    </button>
    <br />
    <button class="button-default-style" @click="toggleDirection()">
      Toggle Direction
    </button>
  </div>
</template>

<script setup lang="ts">
import gsap from "gsap";
const boxA = ref();
let tween: any;

const startFromEnd = () => {
  tween.reverse();
};

const toggleDirection = () => {
  tween.reversed(!tween.reversed());
};

onMounted(() => {
  tween = gsap.to(boxA.value, {
    x: 300,
    duration: 3,
    backgroundColor: "#560563",
    borderRadius: "50%",
    //ease controls the type of end to the animation
    //it too is reverted with the animation
    ease: "elastic",
  });
});

onUnmounted(() => {
  tween.revert();
});
</script>

<style scoped></style>
