<template>
  <button
    class="ac-btn"
    :class="[`ac-btn-${type}`, { 'ac-btn-active': isClick }]"
    @click="onClicks"
  >
    <slot />
  </button>
</template>

<script setup lang="ts">
import { defineProps, ref } from "vue";
defineProps({
  type: {
    type: String,
    default: "default",
  },
  disabled:{
    type: Boolean,
    default: false
  }
});

const isClick = ref(false);

const onClicks = () => {
  isClick.value = true;
  setTimeout(() => {
    isClick.value = false;
  }, 400);
};
</script>

<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$red: #ff4d4f;
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
  &:hover {
    border-color: $blue;
    color: $blue;
  }
  &.ac-btn-active {
    animation: acBtnShadow 0.4s linear;
  }
}
.ac-btn-primary {
  background-color: $blue;
  box-shadow: 0 1px 0 fade-out($color: $blue, $amount: 0.95);
  color: white;
  &:hover {
    border-color: $blue;
    color: white;
  }
  &.ac-btn-active {
    animation: acPrimaryBtnShadow 0.4s linear;
  }
}
.ac-btn-danger {
  background-color: $red;
  box-shadow: 0 1px 0 fade-out($color: $red, $amount: 0.95);
  color: white;
  &:hover {
    border-color: $red;
    color: white;
  }
  &.ac-btn-active {
    animation: acBtnDangerShadow 0.4s linear;
  }
}
@keyframes acBtnShadow {
  0% {
    box-shadow: 0px 0px 6px $blue;
  }
  50% {
    box-shadow: 0px 0px 10px $blue;
  }
  100% {
    box-shadow: 0px 0px 0px $blue;
  }
}
@keyframes acPrimaryBtnShadow {
  0% {
    box-shadow: 0px 0px 6px $blue;
  }
  50% {
    box-shadow: 0px 0px 10px $blue;
    background-color: #0000f5;
  }
  100% {
    box-shadow: 0px 0px 0px $blue;
  }
}
@keyframes acBtnDangerShadow {
  0% {
    box-shadow: 0 2px 6px fade-in($color: $red, $amount: 0.95);
  }
  50% {
    box-shadow: 0 2px 10px fade-in($color: $red, $amount: 0.95);
    background-color: #a40000;
  }
  100% {
    box-shadow: 0px 0px 0px $red;
  }
}
</style>
