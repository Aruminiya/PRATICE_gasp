<template>
  <main class="container mx-auto h-full">
    <div class="grid grid-cols-12 gap-4 h-full">
      <section class="col-span-12 sm:col-span-3 shadow-xl">
        <div class="mt-12 px-3" v-for="{ link, name } in links" :key="link.name">
          <NuxtLink :to="link">
            <UButton class="my-3 w-full" variant="soft">
              <p class="text-center w-full">{{ name }}</p>
            </UButton>
          </NuxtLink>
        </div>
      </section>
      <section class="col-span-12 sm:col-span-9">
        <slot />
      </section>
    </div>
  </main>
</template>

<script setup>
const links = ref([
  {
    link: '/gasp/registerEffect',
    name: 'registerEffect',
  }
]);
</script>