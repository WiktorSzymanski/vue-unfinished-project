<template>
  <div>
    <ul class="nav">
      <li>
        <router-link to="/">
          Home
        </router-link>
      </li>
      <li>
        <router-link to="/about">
          O nas
        </router-link>
      </li>
      <li>
        <router-link to="/offer">
          Oferta
        </router-link>
      </li>
      <li>
        <router-link to="/gallery">
          Galeria
        </router-link>
      </li>
      <li>
        <router-link to="/contact">
          Kontakt
        </router-link>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.nav {
  min-width: 600px;
}

li:hover {
  color: rgb(255, 172, 172);
}

.router-link-exact-active {
  font-weight: 800;
  font-size: 110%;
  color: rgb(255, 172, 172);
}

ul {
  display: flex;
  justify-content: space-around;
}

li {
  font-family: Poppins;
  list-style: none;
  display: inline-flex;
  color: white;
  font-size: 120%;
  min-width: 100px;
  justify-content: center;
  align-items: center;
}

.menu-button {
  height: 50%;
  cursor: pointer;
}
</style>
