<template>
  <template v-if="open">
    <div class="ac-dialog-back"/>
    <div @click="onCloseDialog" class="ac-dialog-pos">
      <div :style="{width: width}" class="ac-dialog">
        <div class="ac-dialog-msg">
          <header>{{ title }}</header>
          <main>
            <slot/>
          </main>
          <footer>
            <Button type="primary">确定</Button>
            <Button>取消</Button>
          </footer>
        </div>
      </div>
    </div>
  </template>
</template>

<script setup lang="ts">
import Button from "./Button.vue";

const props = defineProps({
  title: {
    type: String
  },
  open: {
    type: Boolean,
    default: false
  },
  width: {
    type: String,
    default: '500px'
  },
  closeOnClickOverlay: {
    type: Boolean,
    default: true
  }
});
const emits = defineEmits(["update:open"]);
const onCloseDialog = ()=>{
  if (!props.closeOnClickOverlay)return;
  emits('update:open', false);
}
</script>

<style lang="scss">
.ac-dialog-back {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background-color: rgba(0, 0, 0, .45);
}

.ac-dialog-pos {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1000;

  & > .ac-dialog {
    margin: 0 auto;
    width: auto;
    position: relative;
    top: 100px;
    box-shadow: 0 6px 16px 0 rgba(0, 0, 0, 0.1);

    & > .ac-dialog-msg {
      border-radius: 8px;
      background-color: #fff;
      box-sizing: border-box;
      padding: 20px 24px;

      & > header {
        color: rgba(0, 0, 0, .88);
        background: #fff;
        border-radius: 8px 8px 0 0;
        margin-bottom: 8px;
        font-weight: 600;
        font-size: 16px;
        line-height: 1.5;
        word-wrap: break-word;
      }

      & > main {
        font-size: 14px;
        line-height: 1.5714285714285714;
        word-wrap: break-word;
        color: #000000e0;
      }

      & > footer {
        text-align: end;
        background: 0 0;
        margin-top: 12px;
      }
    }
  }
}
</style>