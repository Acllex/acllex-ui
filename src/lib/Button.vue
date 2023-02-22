<template>
  <button class="ac-btn" :class="[`ac-btn-${type}`, {'ac-btn-active': isClick}]" @click="onClicks"><slot /></button>
</template>

<script setup lang="ts">
import { defineProps, ref } from "vue";
defineProps({
  type: {
    type: String,
    default: "default",
  },
});

const isClick = ref(false);

const onClicks = () => {
  isClick.value = true;
  setTimeout(() => {
    isClick.value = false;
  }, 100);
  console.log("click");
};
</script>

<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$radius: 4px;
.ac-btn {
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  justify-content: center;
  align-items: center;
  white-space: nowrap;
  background: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out($color: #000000, $amount: 0.95);
  & + & {
    margin-left: 8px;
  }
}
.ac-btn-primary {
  background-color: $blue;
  color: white;
}
.ac-btn-active{
  background-color: #038dff;
  color: white;
  border-color: $blue;
}
</style>
