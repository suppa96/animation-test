<template>
  <div>
    <h1>Animation using Context</h1>
    <p class="text-justify max-w-screen-sm mb-10">
      The <b>animation context</b> contains all the animations active inside the
      DOM element we use as context.<br />
      This allows us to scope the animation process (i.e. gsap will not need to
      look through all the document, but only inside the template we marked as
      context).<br />
      This also allows us to not to have to use the ref for every single DOM
      element.<br />
    </p>
    <p class="text-justify max-w-screen-sm mb-10">
      Timelines are sequences of animations, each starting after the earlier
      one. Usually animations start onMounted, but with timelines they appear
      sequentially. To delay, I can use the delay property ore the "position"
      property, which defines the point in the timeline in which the subsequent
      animation is going to happen.
    </p>
    <div
      ref="main"
      class="mt-40 flex flex-col justify-center items-center gap-2"
    >
      <div class="box h-10 w-10 bg-red-500"></div>
      <div class="box h-10 w-10 bg-green-500"></div>
      <div class="box h-10 w-10 bg-blue-500"></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import gsap from "gsap";

definePageMeta({
  title: "Context Animation",
});

const main = ref(); // a template ref used to refer the animation context to a DOM element
let ctx; // the variable which will actually contain the context --> we will use it onUnmount to revert the animation, unhooking gsap
let tl = gsap.timeline({
  yoyo: true,
  repeat: -1,
}); // the variable which is going to store the timeline element

onMounted(() => {
  ctx = gsap.context((self) => {
    const boxes = self.selector!(".box");

    tl.to(boxes[0], { x: 120, rotation: 360 })
      .to(boxes[1], { x: -120, rotation: -360 }, "<") // THE LAST ONE IS A POSITION PARAMETER THAT STARTS WITH THE PREVIOUS ELEMENT
      .to(boxes[2], { y: -166 })
      .reverse();
  }, main.value); // <-- scope!! (allows us to use the animation only inside said DOM element. Plus, we can select the stuff inside using query selectors, without ref
  tl.play();
});
</script>

<style scoped></style>
s
