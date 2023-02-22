<template>
  <div class="docs">
    <aside>
      <ul>
        <li v-for="(value, key) in menuList" :key="key" :class="{active: key==isActive}">
          <router-link :to="value" @click="()=>isActive=key">{{ key }}</router-link>
        </li>
      </ul>
    </aside>
    <div class="doc-info">
      <router-view></router-view>
    </div>
  </div>
</template>

<script setup lang="ts">
import { inject, ref, Ref } from "vue";
const isActive = ref('');
const menuList = ref({
  "Switch 组件": "/doc/switch",
  "Button 组件": "/doc/button",
  "Diglog 组件": "/doc/switch",
});
</script>

<style scoped lang="scss">
$blue: #40a9ff;

.docs {
  display: flex;
  & > aside {
    width: 300px;
    & > ul {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-top: 20px;
      & > li {
        width: 160px;
        border-radius: 8px;
        padding: 10px 0px;
        display: flex;
        justify-content: center;
        &:hover{
          color: $blue;
        }
        &.active{
          color: $blue;
          background-color: rgba($color: $blue, $alpha: .2);
        }
      }
    }
  }
  &>.doc-info{
    padding: 20px 12px;
  }
}
</style>
