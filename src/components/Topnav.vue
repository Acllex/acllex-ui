<template>
  <header>
    <div class="menu">
      <div>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-caidan"></use>
        </svg>
      </div>
    </div>
    <div class="logo" @click="setMenu">
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
</template>

<script setup lang="ts">
import { inject,Ref } from 'vue';


const isMenu = inject<Ref<boolean>>('isMenu');
  const setMenu = ()=>{  
     isMenu!.value = !isMenu!.value;
  }
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
  padding: 60px 10px 30px 20px;
  position: fixed;
  top: 0;
  left: 0;
}
</style>
