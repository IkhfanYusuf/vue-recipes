<template>
  <div class="home">
    <!-- <img class="m-auto w-1/2 md:w-1/6" alt="koala" src="../assets/koala.png" />
    <Welcome /> -->
    <Hero />

    <!-- Main modal -->
    <div
      v-if="showModal"
      id="default-modal"
      aria-hidden="true"
      class="
        transition
        duration-500
        ease-in-out
        flex
        transform
        overflow-x-hidden overflow-y-auto
        h-modal
        absolute
        md:h-full
        top-4
        left-0
        right-0
        md:inset-0
        z-50
        justify-center
        items-center
      "
    >
      <div class="relative w-full max-w-4xl px-4 h-full md:h-auto">
        <!-- Modal content -->
        <div class="bg-white rounded-lg shadow relative dark:bg-gray-700">
          <!-- Modal header -->
          <div
            class="
              flex
              items-start
              justify-between
              p-4
              rounded-t
              dark:border-gray-600
            "
          >
            <h3
              class="
                text-gray-600 text-lg
                lg:text-2xl
                font-semibold
                dark:text-white
              "
            ></h3>
            <button
              @click="setShowModal"
              type="button"
              class="
                text-gray-400
                bg-transparent
                hover:bg-gray-200 hover:text-gray-900
                rounded-lg
                text-sm
                p-1.5
                ml-auto
                inline-flex
                items-center
                dark:hover:bg-gray-600 dark:hover:text-white
              "
              data-modal-toggle="default-modal"
            >
              <svg
                class="w-5 h-5"
                fill="currentColor"
                viewBox="0 0 20 20"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fillRule="evenodd"
                  d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                  clipRule="evenodd"
                />
              </svg>
            </button>
          </div>
          <form>
            <!-- Modal body -->
            <div class="px-6 space-y-2">
              <h2 class="font-semibold mb-6">{{ recipeDetail.title }}</h2>
              <h4 class="font-semibold text-sm text-left">Bahan :</h4>
              <ul class="text-left mb-4">
                <li v-for="(item, index) in recipeDetail.ingredient">
                  {{ index + 1 }}). {{ item }}
                </li>
              </ul>
              <h4 class="font-semibold text-sm text-left">Langkah-langkah :</h4>
              <ul class="text-left mb-4">
                <li v-for="(item, index) in recipeDetail.step">
                  {{ index + 1 }}). {{ item }}
                </li>
              </ul>
            </div>
          </form>
        </div>
      </div>
    </div>

    <!-- <div modal-backdrop class="bg-gray-900 bg-opacity-50 dark:bg-opacity-80 fixed inset-0 z-40" /> -->

    <div class="container grid grid-cols-10 gap-4 px-4 w-11/12 m-auto mt-8">
      <div
        @click="setShowModal(item.key)"
        v-for="item in recipes"
        class="
          col-span-2
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
            <span class="text-xs opacity-50 font-semibold">{{
              item.times
            }}</span>
            <span class="text-xs opacity-50 font-semibold">{{
              item.portion
            }}</span>
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
      recipes: "",
      recipeDetail: "",
      showModal: false,
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
    async getDetailRecipe(key) {
      try {
        const recipes = await Axios.get(`${this.baseUrl}/api/recipe/${key}`);
        this.recipeDetail = recipes.data.results;
        console.log(recipes.data.results);
      } catch (error) {
        console.log(error);
      }
    },

    setShowModal(key) {
      !this.showModal && this.getDetailRecipe(key);

      this.showModal = !this.showModal;
    },
  },
  mounted() {
    this.getRecipes();
  },
};
</script>
