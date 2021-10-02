<template>
  <div class="container">
    <div class="wrapper">
      <div class="flex">
        <router-link class="logo" to="/">UNJICA</router-link>
        <div class="flex">
          <router-link class="nav-item" to="/">{{ $t('menu.home') }}</router-link>
          <router-link class="nav-item" to="/About">{{ $t('menu.about') }}</router-link>
          <router-link class="nav-item" to="/Contact">{{ $t('menu.contact') }}</router-link>
          <locale-switcher class="nav-item" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LocaleSwitcher from './LocaleSwitcher'

export default {
  name: 'Nav',
  components: {
    LocaleSwitcher
  }
}
</script>

<style scoped lang="scss">
@import '../styles/_variables.scss';

.container {
  background-color: $dark-color;
  color: $lilac-color;
  padding: 20px 0;
}
.flex {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.nav-item {
  color: $lilac-color;
  text-decoration: none;
  padding: 10px;
}
.logo {
  text-decoration: none;
  color: $lilac-color;
  font-size: 35px;
}
</style>
