<template>
  <div class="home">
    <!-- <img class="m-auto w-1/2 md:w-1/6" alt="koala" src="../assets/koala.png" />
    <Welcome /> -->
    <Hero @click="handleSearch" />

    <div class="container px-4 m-auto mt-8 pb-8">
      <div v-if="recipes" class="grid grid-cols-10 gap-4">
        <router-link
          :to="'/recipe-detail/' + item.key"
          v-for="item in recipes"
          class="
            col-span-5
            md:col-span-2
            m-auto
            shadow-2xl
            rounded-lg
            overflow-hidden
            bg-green-50
          "
        >
          <img class="" :src="item.thumb" :alt="item.thumb" />
          <div class="p-4">
            <h4 class="font-semibold text-sm mb-4 text-black opacity-70">
              {{ item.title.substring(0, 40) }}.....
            </h4>
            <div class="flex justify-between">
              <span class="text-xs opacity-50 font-semibold flex items-center">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4 mr-1 opacity-40"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
                  />
                </svg>
                <small class="text-xs">{{ item.times }}</small></span
              >
              <span class="text-xs opacity-50 font-semibold flex">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4 mr-1 opacity-40"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M21 15.546c-.523 0-1.046.151-1.5.454a2.704 2.704 0 01-3 0 2.704 2.704 0 00-3 0 2.704 2.704 0 01-3 0 2.704 2.704 0 00-3 0 2.704 2.704 0 01-3 0 2.701 2.701 0 00-1.5-.454M9 6v2m3-2v2m3-2v2M9 3h.01M12 3h.01M15 3h.01M21 21v-7a2 2 0 00-2-2H5a2 2 0 00-2 2v7h18zm-3-9v-2a2 2 0 00-2-2H8a2 2 0 00-2 2v2h12z"
                  />
                </svg>
                <small class="text-xs">
                  {{ item.portion ? item.portion : item.serving }}
                </small>
              </span>
            </div>
          </div>
        </router-link>
      </div>

      <div v-else class="grid grid-cols-10 gap-4">
        <div
          class="
            w-full
            col-span-5
            md:col-span-2
            m-auto
            shadow-2xl
            rounded-lg
            overflow-hidden
            bg-green-50
            animate-pulse
          "
        >
          <div class="h-24 bg-blue-100 rounded-xl m-4 mb-0"></div>
          <div class="p-4">
            <div class="h-3 bg-blue-100 rounded-full mb-2"></div>
            <div class="h-3 bg-blue-100 rounded-full mb-4"></div>
            <div class="flex justify-between">
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
            </div>
          </div>
        </div>
        <div
          class="
            w-full
            col-span-5
            md:col-span-2
            m-auto
            shadow-2xl
            rounded-lg
            overflow-hidden
            bg-green-50
            animate-pulse
          "
        >
          <div class="h-24 bg-blue-100 rounded-xl m-4 mb-0"></div>
          <div class="p-4">
            <div class="h-3 bg-blue-100 rounded-full mb-2"></div>
            <div class="h-3 bg-blue-100 rounded-full mb-4"></div>
            <div class="flex justify-between">
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
            </div>
          </div>
        </div>
        <div
          class="
            w-full
            col-span-5
            md:col-span-2
            m-auto
            shadow-2xl
            rounded-lg
            overflow-hidden
            bg-green-50
            animate-pulse
          "
        >
          <div class="h-24 bg-blue-100 rounded-xl m-4 mb-0"></div>
          <div class="p-4">
            <div class="h-3 bg-blue-100 rounded-full mb-2"></div>
            <div class="h-3 bg-blue-100 rounded-full mb-4"></div>
            <div class="flex justify-between">
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
            </div>
          </div>
        </div>
        <div
          class="
            w-full
            col-span-5
            md:col-span-2
            m-auto
            shadow-2xl
            rounded-lg
            overflow-hidden
            bg-green-50
            animate-pulse
          "
        >
          <div class="h-24 bg-blue-100 rounded-xl m-4 mb-0"></div>
          <div class="p-4">
            <div class="h-3 bg-blue-100 rounded-full mb-2"></div>
            <div class="h-3 bg-blue-100 rounded-full mb-4"></div>
            <div class="flex justify-between">
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
            </div>
          </div>
        </div>
        <div
          class="
            w-full
            col-span-5
            md:col-span-2
            m-auto
            shadow-2xl
            rounded-lg
            overflow-hidden
            bg-green-50
            animate-pulse
          "
        >
          <div class="h-24 bg-blue-100 rounded-xl m-4 mb-0"></div>
          <div class="p-4">
            <div class="h-3 bg-blue-100 rounded-full mb-2"></div>
            <div class="h-3 bg-blue-100 rounded-full mb-4"></div>
            <div class="flex justify-between">
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
              <div class="h-3 w-1/4 bg-blue-100 rounded-full"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Welcome from "@/components/Welcome.vue";
import Hero from "@/components/Hero.vue";
import Axios from "axios";

export default {
  name: "Home",
  components: { Hero },
  data() {
    return {
      baseUrl:
        "https://cors-anywhere.herokuapp.com/masak-apa.tomorisakura.vercel.app",
      recipes: null,
    };
  },
  methods: {
    async getRecipes() {
      try {
        const recipes = await Axios.get(`${this.baseUrl}/api/recipes`);
        this.recipes = recipes.data.results;
        console.log(recipes.data.results);
      } catch (error) {
        console.log(error);
      }
    },
    async handleSearch(keyword) {
      try {
        this.recipes = null;
        const recipes = await Axios.get(
          `${this.baseUrl}/api/search/?q=${keyword}`
        );
        this.recipes = recipes.data.results;
        console.log(recipes.data.results);
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {
    this.getRecipes();
    document.title = "Vue Recipes";
  },
};
</script>
