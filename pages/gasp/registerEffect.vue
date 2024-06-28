<template>
  <div class="box box1 bg-red-500 m-3 w-32 h-32">Box 1</div>
  <div class="box box2 bg-blue-500 m-3 w-32 h-32">Box 2</div>
  <div class="box box3 bg-yellow-500 m-3 w-32 h-32">Box 3</div>
</template>

<script setup>
import gsap from 'gsap';

// isTweening 檢查是否正在動畫中
let box1AnumateStatus = ref('123');
const isBox1Move = function () {
  box1AnumateStatus = gsap.isTweening(".box1");
  console.log(box1AnumateStatus);
};

onMounted(() => {
  gsap.to('.box1', {
    x: 100, 
    ease: 'power2.out',  // 速度曲線
    duration: 1,         // 動畫時間 預設單位：秒
    delay: 0,            // 延遲 預設單位：秒
    repeat: 2,           // 重複播放動畫幾次，無限：-1
  });

  gsap.from('.box2', {
    x: 100, 
    ease: 'power2.out',  // 速度曲線
    duration: 1,         // 動畫時間 預設單位：秒
    delay: 0,            // 延遲 預設單位：秒
    repeat: 2,           // 重複播放動畫幾次，無限：-1
  });
});

</script>
