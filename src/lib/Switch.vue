<template>
  <button :class="{checked: props.checked}" @click="setChecked"><span></span></button>
</template>

<script setup lang="ts">
import { ref } from "vue";
const props = defineProps(['checked'])
const emit = defineEmits(['submit'])
const setChecked = ()=>{
  emit("submit", !props.checked);
}
</script>

<style lang="scss" scoped>
$h: 22px;
$h2: $h - 4px;

button {
  height: $h;
  width: $h * 2;
  border: none;
  background-color: rgba(0,0,0,.45);
  border-radius: $h / 2;
  position: relative;
  span {
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background-color: white;
    border-radius: $h2/2;
    transition: left .5s;
  }
}
button.checked > span {
  left: calc(100% - #{$h2} - 2px);
}
.checked{
  background-color: #4096ff;
}
</style>
