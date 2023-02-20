<template>
  <div class="">
    <div>
      <h1>AcllexUI</h1>
      <h2>一个Vue3的前端 UI 框架</h2>
      <p class="action">
        <a href="">GitHub</a>
        <a href="">开始</a>

      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { inject,Ref } from 'vue';

const isMenu = inject<Ref<boolean>>('isMenu');
console.log(isMenu?.value);

</script>