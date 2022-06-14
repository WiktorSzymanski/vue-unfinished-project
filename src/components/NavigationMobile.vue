<template>
  <div class="navigation-mobile">
    <ul>
      <li class="nav-item">
        <router-link
          to="/"
          @click.native="onClickButton()"
        >
          Home
        </router-link>
      </li>
      <li class="nav-item">
        <router-link
          to="/about"
          @click.native="onClickButton()"
        >
          O nas
        </router-link>
      </li>
      <!-- <li class="nav-item">
        <router-link
          to="/offer"
          @click.native="onClickButton()"
        >
          Oferta
        </router-link>
      </li> -->
      <li class="nav-item">
        <router-link
          to="/gallery"
          @click.native="onClickButton()"
        >
          Galeria
        </router-link>
      </li>
      <li class="nav-item">
        <router-link
          to="/contact"
          @click.native="onClickButton()"
        >
          Kontakt
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  methods: {
    onClickButton() {
      this.$emit('clicked')
    }
  }
}
</script>

<style scoped>
*{
  font-size: 30px;
  z-index: 2;
}

.navigation-mobile {
  position: fixed;
  right: 0;
  top: 50px;
  width: 100%;
  height: 100%;
  background: rgba(52, 58, 64, 0.98);
  transform: translateX(100vw);
  transition: all .5s ease-in-out;
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
  margin-top: 20px;
}

.nav-item:hover {
  color: rgb(255, 81, 81);
}

.router-link-exact-active {
  font-weight: 800;
  font-size: 110%;
  color: rgb(255, 81, 81);
}

.navigation-mobile.open {
  transform: translateX(0px)
}
</style>
