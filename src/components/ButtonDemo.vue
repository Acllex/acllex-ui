<template>
  <div class="button-demo">
    <h1>基础示例</h1>
    <div class="mb-1">
      <Button>基础按钮</Button>
      <Button type="primary">主按钮</Button>
      <Button type="danger">危险按钮</Button>
    </div>
    <br>
    <div class="mb-2">
      <Button plain>基础按钮</Button>
      <Button type="primary" plain>主按钮</Button>
      <Button type="danger" plain>危险按钮</Button>
    </div>
    <h1>禁用状态</h1>
    <div class="mb-1">
      <Button disabled>基础按钮</Button>
      <Button type="primary" disabled>主按钮</Button>
      <Button type="danger" disabled>危险按钮</Button>
    </div>
    <br>
    <div class="mb-2">
      <Button plain disabled>基础按钮</Button>
      <Button type="primary" disabled plain>主按钮</Button>
      <Button type="danger" disabled plain>危险按钮</Button>
    </div>
    <h1>loading状态</h1>
    <div class="mb-1">
      <Button type="primary" loading>主按钮</Button>
      <Button type="danger" loading>危险按钮</Button>
    </div>
    <br>
    <div class="mb-1">
      <Button @click="onclick" type="primary" :loading="loading">主按钮</Button>
    </div>
  </div>

</template>

<script setup lang="ts">
import Button from "../lib/Button.vue";
import {ref} from "vue";
const loading = ref(false);
const onclick = ()=>{
  loading.value = true;
  setTimeout(()=>loading.value=false, 2000);
}
</script>
<style scoped lang="scss">
.button-demo{
  &>.mb-1{
    margin-bottom: 4px;
  }
  & >.mb-2{
    margin-bottom: 8px;
  }
  & > h1{
    padding: 8px 0;
  }
}
</style>