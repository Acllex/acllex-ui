<template>
    <div>
        <Switch :checked="checked" @submit="checked=$event"></Switch>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Switch from "../lib/Switch.vue";
const checked = ref(false);

</script>