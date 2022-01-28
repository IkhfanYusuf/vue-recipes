<template>
  <h1 class="text-5xl md:text-7xl font-bold leading-tight">Masak Apa</h1>
  <h1 class="text-5xl md:text-7xl font-bold leading-tight">Hari Ini?</h1>
  <p class="m-auto w-full px-4 md:w-1/2 text-sm">
    Web ini dibuat untuk belajar vue.js x tailwindcss. Web ini menyediakan
    content tentang resep masakan yang mengambil data dari API
    <a
      class="text-blue-600"
      href="https://github.com/tomorisakura/unofficial-masakapahariini-api"
      >https://github.com/tomorisakura/unofficial-masakapahariini-api</a
    >
  </p>
  <div class="my-2">
    <div class="search relative w-full md:w-1/3 mx-auto px-4">
      <form @submit.prevent="$emit('click', keyword)">
        <input
          v-model="keyword"
          type="text"
          class="
            px-4
            py-2
            text-sm
            bg-transparent
            rounded-full
            w-full
            border-2 border-green-300
            focus:outline-none focus:border-green-400
          "
          placeholder="cari resep"
        />
        <button class="absolute right-8 h-full">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 text-green-400 z-10"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
      </form>
    </div>

    <span class="text-xs"
      >created with
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-5 w-5 inline-block"
        viewBox="0 0 20 20"
        fill="salmon"
      >
        <path
          fill-rule="evenodd"
          d="M3.172 5.172a4 4 0 015.656 0L10 6.343l1.172-1.171a4 4 0 115.656 5.656L10 17.657l-6.828-6.829a4 4 0 010-5.656z"
          clip-rule="evenodd"
        />
      </svg>
      by Ikhfan Yusuf</span
    >
  </div>
</template>

<script>
export default {
  name: "Hero",
  data() {
    return {
      keyword: "",
    };
  },
  emits: ["click"],
};
</script>
