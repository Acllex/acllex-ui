<template>
  <div class="dialog-demo">
    <h1>基础示例</h1>
    <div class="mb-1">
      <Button @click="onclick">Dialog</Button>
      <Dialog v-model:open="isOpen" title="示例1" >
        <p>11111111</p>
        <p>111222222</p>
      </Dialog>
    </div>
    <br>
    <h1>自定义宽度</h1>
    <div class="mb-1">
      <Button @click="()=>{isOpen1 = !isOpen1}">自定义宽度</Button>
      <Dialog width="800px" v-model:open="isOpen1">
        <p>11111111</p>
        <p>111222222</p>
      </Dialog>
    </div>
    <br>
    <h1>确定和取消的回调</h1>
    <div class="mb-1">
      <Button @click="()=>{isOpen2 = !isOpen2}">自定义宽度</Button>
      <Dialog v-model:open="isOpen2" title="确定和取消的回调" :on-ok="onOk" :on-cancel="onCancel">
        <p>11111111</p>
        <p>111222222</p>
      </Dialog>
    </div>
    <br>
    <h1>禁止点击遮罩层关闭</h1>
    <div class="mb-1">
      <Button @click="()=>{isOpen3 = !isOpen3}">自定义宽度</Button>
      <Dialog v-model:open="isOpen3" :closeOnClickOverlay="false">
        <p>11111111</p>
        <p>111222222</p>
      </Dialog>
    </div>
  </div>

</template>

<script setup lang="ts">
import Button from "../lib/Button.vue";
import Dialog from "../lib/Dialog.vue";
import {ref} from "vue";

const isOpen = ref(false);
const isOpen1 = ref(false);
const isOpen2 = ref(false);
const isOpen3 = ref(false);
const onclick = () => {
  isOpen.value = !isOpen.value;
}
const onOk = ()=>{
  console.log("onOk!!!!")
}
const onCancel = ()=>{
  console.log("onCancel!!!!!")
  return false;
}
</script>
<style scoped lang="scss">
.dialog-demo {
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