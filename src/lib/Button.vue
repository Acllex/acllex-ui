<template>
  <button
    class="ac-btn"
    :class="[`ac-btn-${type}`, { 'ac-btn-active': isClick, 'ac-btn-disabled': disabled, 'ac-btn-plain': plain, 'ac-btn-loading': loading }]"
    @click="onClicks"
  >
    <div :class="{'ac-btn-loading': loading}" />
    <slot />
  </button>
</template>

<script setup lang="ts">
import { defineProps, ref } from "vue";
const props = defineProps({
  type: {
    type: String,
    default: "default",
  },
  disabled:{
    type: Boolean,
    default: false
  },
  plain:{
    type: Boolean,
    default: false
  },
  loading: {
    type: Boolean,
    default: false
  }
});

const isClick = ref(false);

const onClicks = () => {
  if(props.disabled||props.loading)return;
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
  &.ac-btn-active {
    animation: acBtnShadow 0.4s linear;
  }
  &.ac-btn-loading{
    cursor: wait;
  }
  &>.ac-btn-loading{
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 4px;
    border-radius: 8px;
    border-color: #fff #fff #fff rgba(0, 0, 0, 0);
    border-style: solid;
    border-width: 2px;
    animation: loading 1s infinite linear;
  }
}
.ac-btn-default{
  $disabled-color: #a8abb2;
  &.ac-btn-disabled{
    color: $disabled-color;
    cursor: not-allowed;
    background-image: none;
    background-color: #fff;
    border-color: #e4e7ed;
    &:hover{
      border-color: #e4e7ed;
      color: $disabled-color;
    }
  }
  &:hover {
    border-color: $blue;
    color: $blue;
  }
}
.ac-btn-primary {
  background-color: $blue;
  box-shadow: 0 1px 0 fade-out($color: $blue, $amount: 0.95);
  color: white;
  &.ac-btn-plain{
    border-color: $blue;
    color: $blue;
    background-color: #ecf5ff;
    &.ac-btn-disabled{
      color: #a0cfff;
      cursor: not-allowed;
      background-image: none;
      background-color: #ecf5ff;
      border-color: #a0cfff;
      &:hover{
        background-color: #ecf5ff;
        border-color: #a0cfff;
        color: #a0cfff;
      }
    }
    &:hover{
      background-color: $blue;
      color: #fff;
    }
  }
  &.ac-btn-disabled{
    color: #fff;
    cursor: not-allowed;
    background-image: none;
    background-color: #a0cfff;
    border-color: #a0cfff;
    &:hover{
      border-color: #a0cfff;
      color: #fff;
    }
  }
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
  &.ac-btn-disabled{
    color: #fff;
    cursor: not-allowed;
    background-image: none;
    background-color: #fab6b6;
    border-color: #fab6b6;
    &:hover{
      border-color: #fab6b6;
      color: #fff;
    }
  }
  &.ac-btn-plain{
    border-color: $red;
    color: $red;
    background-color: #fef0f0;
    &.ac-btn-disabled{
      color: #fab6b6;
      cursor: not-allowed;
      background-image: none;
      background-color: #fef0f0;
      border-color: #fab6b6;
      &:hover{
        background-color: #fef0f0;
        border-color: #fab6b6;
        color: #fab6b6;
      }
    }
    &:hover{
      background-color: $red;
      color: #fff;
    }
  }

  &:hover {
    border-color: $red;
    color: white;
  }
  &.ac-btn-active {
    animation: acBtnDangerShadow 0.4s linear;
  }
}
@keyframes loading {
  0%{
    transform: rotate(0deg);
  }
  100%{
    transform: rotate(360deg);
  }
}
@keyframes acBtnShadow {
  0% {
    box-shadow: 0 0 6px $blue;
  }
  50% {
    box-shadow: 0 0 10px $blue;
  }
  100% {
    box-shadow: 0 0 0 $blue;
  }
}
@keyframes acPrimaryBtnShadow {
  0% {
    box-shadow: 0 0 6px $blue;
  }
  50% {
    box-shadow: 0 0 10px $blue;
    background-color: #0000f5;
  }
  100% {
    box-shadow: 0 0 0 $blue;
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
    box-shadow: 0 0 0 $red;
  }
}
</style>
