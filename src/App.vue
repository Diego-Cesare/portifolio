<script setup>
import Menu from "./components/Menu.vue";
import TopBar from "./components/TopBar.vue";
import Home from "./components/Home.vue";
import About from "./components/About.vue";
import Learn from "./components/Learn.vue";
</script>

<template>
  <div class="container mx-auto h-screen flex">
    <div class="indicator"></div>
    <div class="fixed top-1/2 -translate-y-1/2">
      <Menu />
    </div>
    <div class="w-full h-screen flex flex-col items-end">
      <TopBar />
      <div class="flex flex-col">
        <Home />
        <div class="anime">
          <About />
        </div>
        <div class="anime">
          <Learn />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.anime {
  animation: appear 0.1s;
  animation-timeline: view();
  animation-range: cover 0% cover 50%;
}

.indicator {
  width: .1rem;
  height: 15rem;
  position: fixed;
  top: 50%;
  left: 9%;
  transform: translateY(-50%);
  border-radius: 10px;
  animation: scroll 0.1s;
  animation-timeline: scroll();
  animation-fill-mode: both;
}

@keyframes appear {
  from {
    opacity: 0;
    translate: -100vw 0;
  }
  to {
    opacity: 1;
    translate: 0 0;
  }
}

@keyframes scroll {
  from {
    height: 0;
    background-color: aquamarine;
  }

  to {
    height: 15rem;
    background-color: tomato;
  }
}
</style>
