<template>
  <nav class="bg-white shadow-md px-2 py-3 z-10">
    <div class="container mx-auto flex justify-between items-center">
      <section class="flex justify-center items-center">
        <h1>GASP 測試練習</h1>
      </section>
    </div>
  </nav>
  <div class="grow">
    <NuxtLayout >
      <NuxtPage />
    </NuxtLayout>
  </div>

</template>

<script setup>

</script>

<style>
@import url('./assets/scss/main.scss');

#app {
  height: 100%;
  display: flex;
  flex-direction: column;
}
</style>