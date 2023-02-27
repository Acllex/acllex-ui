<template>
  <button
    class="ac-switch"
    :class="{ checked: props.checked }"
    @click="setChecked"
  >
    <span></span>
  </button>
</template>

<script setup lang="ts">
const props = defineProps(["checked"]);
const emit = defineEmits(["update:checked"]);
const setChecked = () => {
  emit("update:checked", !props.checked);
};
</script>

<style lang="scss">
$h: 22px;
$h2: $h - 4px;

.ac-switch {
  height: $h;
  width: $h * 2;
  border: none;
  background-color: rgba(0, 0, 0, 0.45);
  border-radius: $h / 2;
  position: relative;
  > span {
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background-color: white;
    border-radius: $h2/2;
    transition: left 0.5s;
  }
}

.ac-switch.checked {
  background-color: #4096ff;
  > span {
    left: calc(100% - #{$h2} - 2.4px);
  }
}
</style>
