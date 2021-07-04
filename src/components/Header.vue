<template>
  <header class="text-center bg-green-400 text-gray-700 p-4 mb-10">
    <router-link to="/">
      <div class="text-3xl md:text-5xl font-bold mb-3">
        <i class="fa fa-virus" /> Covid-19 tracker
      </div>
    </router-link>
    <router-link to="/about" class="text-gray-600">About</router-link>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>
