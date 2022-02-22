<template>
  <header>
    <div>
      <span>LOGO</span>
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
</template>

<script lang="ts">
export default {}
</script>

<style lang="scss" scoped>
header{
  width: 100%;
  height: 60px;
  background-color: aqua;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 10px;
  ul{
    display: flex;
    li{
      padding: 0 10px;
    }
  }
}

</style>