<template>
  <div class="container">
    <div class="wrapper">
      <div class="flex">
        <div>UNJICA</div>
        <div class="menu">
          <router-link class="router-link" to="/">Home</router-link>
          <router-link class="router-link" to="/About">About</router-link>
          <router-link class="router-link" to="/Contact">Contact</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav'
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
.router-link {
  color: $lilac-color;
  text-decoration: none;
  padding: 10px;
}
.active {
  color: $dark-color;
  text-decoration: none;
}
</style>
