<template>
  <main class=" container mx-auto">
    <section class="grid grid-cols-9 gap-4 mt-12">
      <!-- 說明區塊 -->
      <section class="col-span-9">
        <h1 class="font-bold">gsap.effects()</h1>
        <h4 class="font-bold my-2">定義你自己的效果</h4>
        <br>
        <p>定義你自己的效果（例如，通過使用 <code>gsap.registerEffect()</code> ）。</p>
        <p>使用這些效果在不同的元素上進行動畫。</p>
      </section>

      <!-- 動畫區塊 -->
      <section class="col-span-9">
        <div class="border-2 rounded-lg w-full h-96 p-2">
          <!-- 方塊 1 -->
          <div class="box box1 w-24 h-24 rounded-lg bg-red-500 flex justify-center items-center">
            <p class="font-bold text-white">方塊 1</p>
          </div>
          <br>
          <!-- 方塊 2 -->
          <div class="box box2 w-24 h-24 rounded-lg bg-blue-500 flex justify-center items-center">
            <p class="font-bold text-white">方塊 2</p>
          </div>
          <br>
          <!-- 方塊 3 -->
          <div class="box box3 w-24 h-24 rounded-lg bg-yellow-500 flex justify-center items-center">
            <p class="font-bold text-white">方塊 3</p>
          </div>
        </div>
      </section>
    </section>
  </main>
</template>

<script setup>
import { gsap } from "gsap";

// 定義屬於自己的 gsap 動畫效果
gsap.registerEffect({
  name: "fade",
  effect: (targets, config) => {
    return gsap.to(targets, { duration: config.duration, delay: config.delay, opacity: 0 });
  },
  defaults: { duration: 2, delay: 0 }, // 默認值會應用到任何傳遞給效果的 "config" 對象
  extendTimeline: true, // 現在你可以直接在任何 GSAP 時間軸上調用這個效果，結果會立即插入到你定義的位置（默認是按順序在末尾）
});
const timeline = ref(null);
const runAnimations = () => {
  // 現在我們可以這樣使用它
  // gsap.effects.fade(".box1");
  // gsap.effects.fade(".box2", { duration: 1, delay: 1 }); // 可以為不同的元素設置不同的配置
  // gsap.effects.to(".box3", { x: 100 });

  // 或直接在 GSAP 時間軸上調用
  let tl = gsap.timeline();
  tl.fade(".box1", { duration: 1 })
    .fade(".box2", { duration: 1 }, "+=1")
    .to(".box3", { x: 100 });
};

const restartAnimations = () => {
  // gasp.set 用於立即設置一個或多個元素的屬性
  gsap.set(".box1, .box2, .box3", { clearProps: "all" });
  runAnimations();
};

onMounted(() => {
  restartAnimations();
});

</script>

<style scoped lang="scss">
 
</style>