<template>
  <div class="user-data">{{ userData.name }} @{{ userData.username }}</div>
  <nav>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/modals">Modals</RouterLink>
    <RouterLink to="/posts">Posts</RouterLink>
  </nav>

  <!-- :userData="userData"  -->
  <RouterView />
  <!-- 
    <router-view v-slot="{ Component }">
  <keep-alive>
    <component :is="Component" />
  </keep-alive>
</router-view>
   -->
</template>

<script setup>
/*
imports
*/
import { reactive, provide } from "vue";
/*
user data
*/
const userData = reactive({
  name: "Danny",
  username: "dannyconnell",
});

provide("userData", userData);
</script>

<style scoped>
nav {
  width: 100%;
  font-size: 30px;
  text-align: center;
  margin-top: 1rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}
.user-data {
  position: absolute;
  background: beige;
  top: 0;
  right: 0;
  font-size: 12px;
  padding: 5px;
}
</style>
