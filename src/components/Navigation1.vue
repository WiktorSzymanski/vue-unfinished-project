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
  font-weight: 700;
  font-size: 105%;
  color: rgb(255, 172, 172);
  transition: all .1s ease-in-out;
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
  min-width: 120px;
  justify-content: center;
  align-items: center;
  transition: all .2s ease-in-out;
}

.menu-button {
  height: 50%;
  cursor: pointer;
}
</style>
