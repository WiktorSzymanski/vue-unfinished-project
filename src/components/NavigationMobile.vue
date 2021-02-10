<template>
  <div class="navigation-mobile">
    <ul>
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
</template>

<style scoped>
.navigation-mobile {
  position: fixed;
  right: 0;
  top: 70px;
  width: 100%;
  height: 100%;
  background: rgba(52, 58, 64, 0.98);
}

ul {
  margin-top: 70px;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

li {
  font-family: Poppins;
  list-style: none;
  color: white;
  font-size: 30px;
}
</style>
