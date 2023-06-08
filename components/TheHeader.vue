<template>
  <header class="w-full bg-green-400 text-black p-3">
    <h1 class="font-bold text-4xl">My GSAP Animation Playground</h1>
    <br />
    <nuxt-link
      to="/"
      class="underline hover:bg-black hover:text-green-400 py-1 px-2"
    >
      Home
    </nuxt-link>
    <nuxt-link
      to="/basic-animation"
      class="underline hover:bg-black hover:text-green-400 py-1 px-2"
    >
      Basic Animation
    </nuxt-link>
    <nuxt-link
      to="/context-animation"
      class="underline hover:bg-black hover:text-green-400 py-1 px-2"
    >
      Context Animation
    </nuxt-link>
    <nuxt-link
      to="/scroll-animation"
      class="underline hover:bg-black hover:text-green-400 py-1 px-2"
    >
      Scroll Animation
    </nuxt-link>
  </header>
</template>
