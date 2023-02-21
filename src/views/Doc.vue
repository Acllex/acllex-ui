<template>
  <div>
    <aside>
      <ul>
        <li
            v-for="(value, key) in menuList"
            :key="key"
        >
          <router-link :to="value">{{ key }}</router-link>
        </li>
      </ul>
    </aside>
  </div>
  <router-view></router-view>
</template>

<script setup lang="ts">
import {inject, ref, Ref} from 'vue';

const menuList = ref({
  "Switch 组件": "/doc/switch",
  "Button 组件": "/doc/button",
  "Diglog 组件": "/doc/switch",
});

</script>