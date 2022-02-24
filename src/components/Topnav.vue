<template>
  <header>
    <div class="menu">
      <div>
        <svg class="icon" aria-hidden="true">
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
        <router-link to="">菜单1</router-link>
      </li>
      <li>
        <router-link to="">菜单2</router-link>
      </li>
    </ul>
  </header>
  <aside>
    <h1>组件列表</h1>
    <h4>Switch 组件</h4>
    <h4>Button 组件</h4>
    <h4>Diglog 组件</h4>
  </aside>
</template>

<script lang="ts">
export default {
  setup(){
    const toggleMenu = ()=>{

    }
  }
}
</script>

<style lang="scss" scoped>

header{
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
  .menu{
    display: none;
  }
  .logo{
    margin: 6px 0;
    display: flex;
    align-items: center;
    svg{
      width: 40px;
      height: 40px;
    }
    span{
      margin-left: 10px;
      font-family: "Dosis", "Source Sans Pro", "Helvetica Neue", Arial, sans-serif;
      font-size: 1.5em;
      font-weight: 500;
      color: #273849;
    }
  }
  ul{
    display: flex;
    li{
      padding: 0 10px;
    }
  }
  @media screen and (max-width: 500px) {
    .menu{
      display: block;
      position: relative;
      div{
        position: absolute;
        width: 34px;
        top: -12px;
        svg{
          width: 26px;
          height: 26px;
        }
      }
    }
    .logo{
      width: 36px;
      height: 36px;
      margin: 6px 0;
      svg{
        width: 100%;
        height: 100%;
      }
      span{
        display: none;
      }
    }
    ul>li{
      display: none;
    }
  }
}
aside{
  padding: 60px 10px 30px 20px;
  position: fixed;
  top: 0;
  left: 0;
}
</style>