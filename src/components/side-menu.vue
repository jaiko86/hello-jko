<template>
  <nav class="side-menu">
    <router-link to="/" class="logo-wrapper">
      <img src="../assets/logo.png" alt="J.Ko logo" class="logo" />
    </router-link>
    <router-link to="/about">About</router-link>
    <router-link to="/timeline">Dev Journey</router-link>
    <router-link to="/sketches">Sketches</router-link>
    <router-link to="/projects">Projects</router-link>
    <router-link to="/work">Work</router-link>
    <router-link to="/thoughts">Thoughts</router-link>
    <router-link to="/links-contacts">Links &amp; Contacts</router-link>
  </nav>
</template>

<script>
export default {
  name: 'SideMenu',
}
</script>

<style lang="scss" scoped>
@import '../style/global.scss';

.side-menu {
  position: fixed; 
  left: 0;
  top: 0;
  width: $menuWidth;
  background: #333;
  height: 100vh;
  a {
    display: block;
    font-size: 20px;
    padding: 10px;
    color: white;
    text-decoration: none;
    border-left: 5px solid transparent;
    &:not(:first-of-type) {
      margin-top: 10px;
    }

    &:hover {
      border-color: gray;
    }

    &.router-link-active:not(.logo-wrapper) {
      border-color: white;
    }
  }
  a.logo-wrapper {
    text-align: center;
    border-left: none;
  }
}
.logo {
  max-width: 100px;
}


</style>