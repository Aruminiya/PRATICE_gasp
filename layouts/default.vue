<template>
  <main class="container mx-auto h-full">
    <div class="grid grid-cols-12 gap-4 h-full">
      <section class="col-span-12 sm:col-span-3 shadow-xl">
        <div class="mt-12 ">
          <div class="px-3" v-for="{ link, name, descript } in links" :key="link.name">
            <NuxtLink :to="link">
              <UTooltip class="w-full" :text="descript" :popper="{ placement: 'right' }">
                <button class="linkBtn transition-colors my-1 py-2 bg-phototaxisBlue-50 hover:bg-phototaxisBlue-100
                  text-phototaxisBlue-500 w-full rounded-lg">
                  <p class="text-center w-full">{{ name }}</p>
                </button>
              </UTooltip>
            </NuxtLink>
          </div>
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
    link: '/gasp/gsapEffects',
    name: 'gsapEffects',
    descript: '定義你自己的效果',
  },
  {
    link: '/gasp/gsapGlobalTimeline',
    name: 'gsapGlobalTimeline',
    descript: '管理和控制所有的動畫。',
  }
]);
</script>

<style scoped lang="scss">
.router-link-exact-active {
  button {
    background-color: $phototaxisBlue-500;
    color: white;
  }
}
</style>