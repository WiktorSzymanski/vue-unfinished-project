<template>
  <div id="app">
    <header class="navbar navbar-light bg-dark">
      <router-link class="navbar-brand" to="/">
        <img src="./assets/logo.svg">
      </router-link>
        <img class="menu-button" src="./assets/logo-short.svg">
    </header>
    <SimpleJumbotron/>
    <div class="navbar-nav navbar-light bg-light">
      <div class="container navbar-main">
        <ul class="nav nav-pills nav-fill">
          <li class="nav-item">
            <router-link to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about">O Nas</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/offer">Oferta</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/gallery">Galleria</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/contact">Kontakt</router-link>
          </li>
        </ul>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-12 content">
          <router-view/>
        </div>
      </div>
    </div>
    <footer class="bg-dark">
      Coś tam
    </footer>
  </div>
</template>

<script>
import SimpleJumbotron from '@/components/SimpleJumbotron.vue';

export default {
  components: {
    SimpleJumbotron,
  },
};
</script>

<style>
.router-link-active {
  outline: none;
}
</style>

<style scoped>
.navbar-brand {
  padding: 10px;
}
.navbar-brand img {
  height: 20px;
}
.navbar-main {
  padding: 5px;
}
.navbar-nav {
  margin-bottom: 30px;
}
.nav-item:hover {
  color: red;
}

li {
  font-family: Poppins;
}

footer {
  font-family: Roboto;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

header {
  height: 80px;
}

.menu-button {
  height: 50%;
  cursor: pointer;
}
</style>
