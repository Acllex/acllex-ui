<template>
  <div class="dialog-demo">
    <h1>基础示例</h1>
    <Button @click="onclick">Dialog</Button>
    <Dialog :open="isOpen" title="示例1">
      <p>11111111</p>
      <p>111222222</p>
    </Dialog>
  </div>

</template>

<script setup lang="ts">
import Button from "../lib/Button.vue";
import Dialog from "../lib/Dialog.vue";
import {ref} from "vue";

const isOpen = ref(false);
const onclick = () => {
  isOpen.value = !isOpen.value;
}
</script>
<style scoped lang="scss">
.button-demo {
  & > .mb-1 {
    margin-bottom: 4px;
  }

  & > .mb-2 {
    margin-bottom: 8px;
  }

  & > h1 {
    padding: 8px 0;
  }
}
</style>