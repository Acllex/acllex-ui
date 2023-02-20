<template>
  <header>
    <div class="menu">
      <div>
        <svg class="icon" @click="setMenu" aria-hidden="true">
          <use xlink:href="#icon-caidan"></use>
        </svg>
      </div>
    </div>
    <div class="logo">
      <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-_UIsheji"></use>
      </svg>
      <span>AcllexUI</span>
    </div>
    <ul>
      <li>
        <router-link to="/">首页</router-link>
      </li>
      <li>
        <router-link to="/doc">文档</router-link>
      </li>
    </ul>
  </header>
  <aside v-if="isMenu" @click="setMenu">
    <li
      :class="selectComputed == value ? 'active' : ''"
      v-for="(value, key) in menuList"
      :key="key"
    >
      <router-link :to="value">{{ key }}</router-link>
    </li>
  </aside>
</template>

<script setup lang="ts">
import { inject, ref, Ref, computed } from "vue";
import { useRoute } from "vue-router";
const menuList = ref({
  首页: "/",
  组件: "/doc",
  "Switch 组件": "/doc/switch",
  "Button 组件": "/doc/switch",
  "Diglog 组件": "/doc/switch",
});

const isMenu = inject<Ref<boolean>>("isMenu");
const setMenu = () => {
  isMenu!.value = !isMenu!.value;
};
const route = useRoute();
const selectComputed = computed(() => {
  console.log(route.fullPath);

  return route.fullPath;
});
</script>

<style lang="scss" scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;
  width: 100%;
  background-color: aliceblue;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 14px;
  .menu {
    display: none;
  }
  .logo {
    margin: 6px 0;
    display: flex;
    align-items: center;
    svg {
      width: 40px;
      height: 40px;
    }
    span {
      margin-left: 10px;
      font-family: "Dosis", "Source Sans Pro", "Helvetica Neue", Arial,
        sans-serif;
      font-size: 1.5em;
      font-weight: 500;
      color: #273849;
    }
  }
  ul {
    display: flex;
    li {
      padding: 0 10px;
    }
  }
  @media screen and (max-width: 500px) {
    .menu {
      display: block;
      position: relative;
      div {
        position: absolute;
        width: 34px;
        top: -12px;
        svg {
          width: 26px;
          height: 26px;
        }
      }
    }
    .logo {
      width: 36px;
      height: 36px;
      margin: 6px 0;
      svg {
        width: 100%;
        height: 100%;
      }
      span {
        display: none;
      }
    }
    ul > li {
      display: none;
    }
  }
}
aside {
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 6px 16px 0 rgb(0 0 0 / 8%), 0 3px 6px -4px rgb(0 0 0 / 12%),
    0 9px 28px 8px rgb(0 0 0 / 5%);
  padding: 12px;
  position: fixed;
  top: 50px;
  left: 0;
  z-index: 12;
  li {
    width: 160px;
    padding: 6px 0;
    display: flex;
    justify-content: center;
    border-radius: 8px;
  }
  .active {
    background-color: #c5e2ff;
    color: #0b85ff;
  }
}
</style>
