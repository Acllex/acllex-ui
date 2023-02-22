<template>
  <div class="button-demo">
    <h1>基础示例</h1>
    <Button>基础按钮</Button>
    <Button type="primary">主按钮</Button>
    <Button type="danger">危险按钮</Button>
  </div>

</template>

<script setup lang="ts">
import Button from "../lib/Button.vue";
</script>
<style scoped lang="scss">
.button-demo{
  & > h1{
    padding: 8px 0;
  }
}
</style>