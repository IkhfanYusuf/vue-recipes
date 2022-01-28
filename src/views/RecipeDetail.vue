<template>
  <div v-if="recipeDetail" class="px-4 pb-6 md:px-10">
    <h2 class="font-bold text-xl md:text-3xl mb-4 md:w-5/12 md:mx-auto">
      {{ recipeDetail.title }}
    </h2>
    <div class="flex justify-between md:w-1/3 md:mx-auto mb-8 px-4">
      <span class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 mr-1 opacity-40"
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
        <small class="text-sm">{{ recipeDetail.times }}</small>
      </span>

      <span class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 mr-1 opacity-40"
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
        <small class="text-sm">{{ recipeDetail.servings }}</small>
      </span>

      <span class="flex items-center">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 mr-1 opacity-40"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M17.657 18.657A8 8 0 016.343 7.343S7 9 9 10c0-2 .5-5 2.986-7C14 5 16.09 5.777 17.656 7.343A7.975 7.975 0 0120 13a7.975 7.975 0 01-2.343 5.657z"
          />
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M9.879 16.121A3 3 0 1012.015 11L11 14H9c0 .768.293 1.536.879 2.121z"
          />
        </svg>
        <small class="text-sm">{{ recipeDetail.dificulty }}</small>
      </span>
    </div>
    <div class="grid grid-cols-12 shadow-xl items-center relative">
      <button
        @click="setView"
        class="
          absolute
          top-0
          bg-green-600
          px-4
          py-2
          text-white text-sm
          font-semibold
        "
      >
        <span v-if="view === 'ingredient'"> Langkah Memasak </span>
        <span v-else> Bahan </span>
      </button>

      <div
        class="
          col-span-12
          md:col-span-4
          text-left
          bg-blue-100 bg-opacity-25
          px-6
          py-12
          order-last
          md:order-first
        "
      >
        <div>
          <h4 class="font-semibold mb-2 text-xl">
            <span v-if="view === 'ingredient'"> Bahan : </span>
            <span v-else> Langkah Memasak : </span>
          </h4>
          <ul v-if="view === 'ingredient'">
            <li v-for="(item, index) in recipeDetail.ingredient">
              {{ index + 1 }}). {{ item }}
            </li>
          </ul>
          <ul v-else>
            <li class="py-1" v-for="item in recipeDetail.step">
              {{ item }}
            </li>
          </ul>
        </div>
      </div>
      <div
        class="
          col-span-12
          md:col-span-8
          text-left
          bg-white bg-opacity-25
          order-first
          md:order-last
        "
      >
        <img
          class="w-full"
          :src="recipeDetail.thumb"
          :alt="recipeDetail.thumb"
        />
      </div>
    </div>
  </div>

  <div v-else class="px-4 pb-6 md:px-10 min-h-screen animate-pulse">
    <h2
      class="
        font-bold
        text-xl
        md:text-3xl
        mb-4
        md:w-5/12 md:mx-auto
        h-8
        bg-blue-100
      "
    ></h2>
    <div class="flex justify-between md:w-1/3 md:mx-auto mb-8 px-4">
      <span class="flex items-center w-24 h-3 bg-blue-100 rounded-full"></span>
      <span class="flex items-center w-24 h-3 bg-blue-100 rounded-full"></span>
      <span class="flex items-center w-24 h-3 bg-blue-100 rounded-full"></span>
    </div>
    <div class="grid grid-cols-12 shadow-xl relative">
      <div
        class="
          col-span-12
          md:col-span-4
          text-left
          bg-blue-100 bg-opacity-25
          px-6
          order-last
          md:order-first
        "
      >
        <div>
          <div
            class="hidden md:block relative -left-6 h-6 w-1/4 mb-24 bg-blue-100"
          ></div>
          <h4
            class="
              mt-8
              md:mt-0
              font-semibold
              mb-4
              text-xl
              h-4
              bg-blue-100
              w-1/3
              rounded-full
            "
          ></h4>
          <ul>
            <li class="h-3 rounded-full bg-blue-100 mb-3"></li>
            <li class="h-3 rounded-full bg-blue-100 mb-3"></li>
            <li class="h-3 rounded-full bg-blue-100 mb-3"></li>
            <li class="h-3 rounded-full bg-blue-100 mb-3"></li>
            <li class="h-3 rounded-full bg-blue-100 mb-3"></li>
          </ul>
        </div>
      </div>
      <div
        class="
          col-span-12
          md:col-span-8
          text-left
          bg-blue-100 bg-opacity-25
          order-first
          md:order-last
        "
      >
        <div class="bg-blue-100 w-full rounded-lg h-60 md:h-96">
          <div
            class="md:hidden relative h-6 w-1/3 mb-24 bg-white bg-opacity-25"
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";

export default {
  name: "RecipeDetail",
  data() {
    return {
      baseUrl:
        "https://cors-anywhere.herokuapp.com/masak-apa.tomorisakura.vercel.app",
      recipeDetail: null,
      key: this.$route.params.slug,
      view: "ingredient",
    };
  },
  methods: {
    async getRecipeDetail() {
      try {
        const recipes = await Axios.get(
          `${this.baseUrl}/api/recipe/${this.key}`
        );
        this.recipeDetail = recipes.data.results;
        console.log(recipes.data.results);
      } catch (error) {
        console.log(error);
      }
    },
    setView() {
      this.view === "ingredient"
        ? (this.view = "step")
        : (this.view = "ingredient");
    },
  },
  mounted() {
    this.getRecipeDetail();
  },
};
</script>
