<template>
  <div>
    <nav class="flex flex-col gap-4">
      <a
        v-for="item in navItems"
        :key="item.id"
        :href="`#${item.id}`"
        :class="[
          'text-2xl font-thin px-2',
          activeSection === item.id ? 'text-blue-400' : 'text-gray-800',
          'hover:text-blue-400 hover:border-blue-400'
        ]"
      >
        {{ item.name }}
      </a>
    </nav>
  </div>
</template>

<script setup>
import { useIntersectionObserver } from "@vueuse/core";
import { ref, onMounted } from "vue";

// Itens do menu
const navItems = [
  { id: "home", name: "Inicio" },
  { id: "about", name: "Sobre" },
  { id: "learn", name: "Aprendendo" },
  { id: "projects", name: "Projetos" },
];

// Estado para armazenar qual seção está visível
const activeSection = ref("home");

// Observar cada seção correspondente
onMounted(() => {
  navItems.forEach((item) => {
    const target = document.getElementById(item.id);

    if (target) {
      useIntersectionObserver(target, ([entry]) => {
          if (entry.isIntersecting) {
            activeSection.value = item.id;
          }
        },{ threshold: 0.6 })}
  });
});
</script>

<style scoped>

</style>
