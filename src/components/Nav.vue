<template>
  <nav>
    <router-link to="/">Vite Recipe Book</router-link>
    <router-link v-for="route in routes" :key="route.path" :to="route.to" :class="{ active: isActive(route.to) }">{{route.text}}</router-link>
  </nav>
</template>

<script>
import { computed } from "vue";
import { useRouter } from "vue-router";

export default {
  setup() {
    const routes = [
      { to: "/ingredients", text: "Ingredients" },
      { to: "/recipes", text: "Recipes" }
    ];
    const router = useRouter();
    const activeRoute = computed(() => router.currentRoute.value.path);
    const isActive = path => path === activeRoute.value
    return { isActive, routes };
  }
};
</script>

<style scoped>
nav {
  border-bottom: 2px solid cadetblue;
  margin-bottom: 2rem;
}

a {
  margin: 1rem;
}
</style>