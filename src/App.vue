<template>
  <Topnav></Topnav>
  <div class="main">
    <router-view/>
  </div>
</template>

<script setup lang="ts">
import Topnav from "./components/Topnav.vue";

import {ref, provide} from "vue";

const width = document.documentElement.clientWidth;
if (width > 500) {
  provide("isMenu", ref<boolean>(false));
} else {
  provide("isMenu", ref<boolean>(false));
}
</script>

<style scoped lang="scss">
.main {
  width: 100%;
  padding-top: 60px;
}
</style>
