<script>
export default {
  name: "Header",
};
</script>


<template>
  <header class="bg-red-500 p-4">
    <nav>
      <ul
        class="flex flex-col w-full items-center lg:grid lg:w-1/3 lg:grid-cols-3 lg:justify-self-end md:grid md:w-1/2 md:grid-cols-3 md:justify-self-end gap-y-6 py-4">
        <li>
          <RouterLink to="/"
            class="inline-block bg-white text-red-500 font-bold py-2 px-4 rounded min-w-[110px] text-center transition-all duration-300 ease-in-out hover:scale-105">
            Startsida</RouterLink>
        </li>
        <li>
          <RouterLink to="/movie"
            class="inline-block bg-white text-red-500 font-bold py-2 px-4 rounded min-w-[110px] text-center transition-all duration-300 ease-in-out hover:scale-105">
            Filmer</RouterLink>
        </li>
        <li>
          <RouterLink to="/about"
            class="inline-block bg-white text-red-500 font-bold py-2 px-4 rounded min-w-[110px] text-center transition-all duration-300 ease-in-out hover:scale-105">
            Om Vue.js</RouterLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped></style>