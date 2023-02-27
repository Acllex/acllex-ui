<template>
  <template v-if="open">
    <div class="ac-dialog-back"/>
    <div @click.stop="onCloseDialog" class="ac-dialog-pos">
      <div :style="{width: width}" class="ac-dialog">
        <div class="ac-dialog-msg">
          <header>
            <span>{{ title }}</span>
            <div class="ac-dialog-close">
              <svg class="icon" aria-hidden="true">
                <use xlink:href="#icon-guanbi"></use>
              </svg>
            </div>

          </header>
          <main>
            <slot/>
          </main>
          <footer>
            <Button type="primary" @click.stop="dialogOk">确定</Button>
            <Button @click.stop="dialogClose">取消</Button>
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
  },
  onOk: {
    type: Function,
    default: () => {
    }
  },
  onCancel: {
    type: Function,
    default: () => {
    }
  }
});
const emits = defineEmits(["update:open"]);
const onClose = () => {
  emits('update:open', false);
}
const onCloseDialog = () => {
  if (!props.closeOnClickOverlay) return;
  onClose();
}
const dialogOk = () => {
  const bool = props.onOk();
  if (bool === false) return;
  onClose();
}
const dialogClose = () => {
  const bool = props.onCancel();
  if (bool === false) return;
  onClose();
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
        & > .ac-dialog-close{
          position: absolute;
          top: 18px;
          right: 18px;
          font-size: 12px;
        }
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