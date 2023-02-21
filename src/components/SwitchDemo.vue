<template>
    <div>
        <Switch v-model:checked="checked"></Switch>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Switch from "../lib/Switch.vue";
const checked = ref(false);

</script>