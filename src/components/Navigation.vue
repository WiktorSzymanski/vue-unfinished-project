<template>
  <div class="navbar-nav navbar-light bg-light">
    <div class="container navbar-main">
      <ul class="nav nav-pills nav-fill">
        <li class="nav-item">
          <router-link to="/">
            Home
          </router-link>
        </li>
        <li class="nav-item">
          <router-link to="/about">
            O nas
          </router-link>
        </li>
        <li class="nav-item">
          <router-link to="/offer">
            Oferta
          </router-link>
        </li>
        <li class="nav-item">
          <router-link to="/gallery">
            Galeria
          </router-link>
        </li>
        <li class="nav-item">
          <router-link to="/contact">
            Kontakt
          </router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

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

.menu-button {
  height: 50%;
  cursor: pointer;
}
</style>
