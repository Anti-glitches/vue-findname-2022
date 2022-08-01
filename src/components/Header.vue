<template>
  <header class="text-center bg-indigo-700 text-white p-8 mb-10">
    <div class="text-3xl font-bold md:text-5xl"><i class="fa-solid fa-magnifying-glass-location"></i>
      Guess Your Country</div>
    <p>API by <a class="text-blue-400" href="https://api.nationalize.io/?name=ilham" target="_blank">nationalize.io</a>
      & <a class="text-blue-400" href="https://restcountries.com/v2/alpha/id" target="_blank">restcountries</a></p>
    <div class="flex text-center justify-center gap-4">
      <router-link to="/" class="text-blue-200">Guess Nationality</router-link>
      <router-link to="/about" class="text-blue-200">Cat Quotes</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
}
</script>