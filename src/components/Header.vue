<template>
  <nav id="nav" class="flex justify-between items-center">
    <router-link to="/" class="flex items-center">
      <img class="w-1/12" src="@/assets/logo.png" alt="vue masak" />
      <span class="ml-2 font-semibold">VueRecipes.</span>
    </router-link>
    <!-- <div>
      <router-link to="/">Home</router-link> |
      <router-link to="/contact">Contact</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
  </nav>
</template>

<script>
export default {
  name: "Header",
};
</script>
