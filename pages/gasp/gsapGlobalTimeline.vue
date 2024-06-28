<template>
  <main class=" container mx-auto">
    <section class="grid grid-cols-9 gap-4 mt-12">
      <!-- 說明區塊 -->
      <section class="col-span-9">
        <h1 class="font-bold">gsap.globalTimeline()</h1>
        <h4 class="font-bold my-2">管理和控制所有的動畫</h4>
        <br>
        <p><code>gsap.globalTimeline()</code> 是 GSAP 提供的一個全局時間軸，可以用來管理和控制所有的動畫。</p>
        <p>你可以將動畫添加到這個全局時間軸中，然後通過控制這個時間軸來控制所有的動畫。</p>
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

      <!-- 動畫控制區塊 -->
      <section class="col-span-9">
        <UButton class="mx-1" @click="restartAnimations">重新播放</UButton>
        <UButton class="mx-1" @click="pauseAnimations">暫停</UButton>
        <UButton class="mx-1" @click="resumeAnimations">繼續</UButton>
        <UButton class="mx-1" @click="speedUpAnimations">加速</UButton>
        <UButton class="mx-1" @click="slowDownAnimations">減速</UButton>
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

const runAnimations = () => {
  // 使用全局時間軸
  gsap.globalTimeline.clear(); // 清除之前的動畫
  gsap.effects.fade(".box1");
  gsap.effects.fade(".box2", { duration: 1, delay: 2 });
  gsap.effects.fade(".box3", { duration: 3, delay: 2 });
};

const restartAnimations = () => {
  // gasp.set 用於立即設置一個或多個元素的屬性
  gsap.set(".box1, .box2, .box3", { clearProps: "all" });
  runAnimations();
};

const pauseAnimations = () => {
  gsap.globalTimeline.pause();
};

const resumeAnimations = () => {
  gsap.globalTimeline.play();
};

const speedUpAnimations = () => {
  gsap.globalTimeline.timeScale(2); // 將時間縮放設置為2倍速
};

const slowDownAnimations = () => {
  gsap.globalTimeline.timeScale(0.5); // 將時間縮放設置為0.5倍速
};

onMounted(() => {
  restartAnimations();
});

</script>

<style scoped lang="scss">
 
</style>