<template>
  <div>Doc</div>
  <router-view></router-view>
</template>

<script setup lang="ts">
import { inject,Ref } from 'vue';

const isMenu = inject<Ref<boolean>>('isMenu');

</script>