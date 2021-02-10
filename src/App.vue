<template>
  <div id="app">
    <div class="content">
      <header class="navbar navbar-light bg-dark">
        <router-link
          v-if="!mobileView"
          class="navbar-brand"
          to="/"
        >
          <img src="./assets/logo.svg">
        </router-link>
        <div />
        <img
          v-if="mobileView"
          class="menu-button"
          src="./assets/logo-short.svg"
          @click="openNav()"
        >
      </header>
      <SimpleJumbotron />
      <Navigation v-if="!mobileView" />
      <div class="container">
        <div class="row">
          <router-view />
        </div>
      </div>
      <Footer />
    </div>
    <NavigationMobile v-if="showNav" />
  </div>
</template>

<script>
import SimpleJumbotron from '@/components/SimpleJumbotron.vue';
import Navigation from '@/components/Navigation.vue';
import NavigationMobile from '@/components/NavigationMobile.vue';
import Footer from '@/components/Footer.vue';

export default {
  components: {
    SimpleJumbotron,
    Navigation,
    NavigationMobile,
    Footer,
  },
  data() {
    return {
      mobileView: false,
      showNav: false,
    };
  },
  watch: {
    mobileView() {
      if (!this.mobileView) {
        this.showNav = false;
      }
    },
  },
  mounted() {
    this.handleView();
    window.addEventListener('resize', this.handleView);
  },
  methods: {
    handleView() {
      this.mobileView = window.innerWidth <= 990;
      document.querySelector('body').classList.remove('no-scroll');
    },
    openNav() {
      if (this.showNav) {
        document.querySelector('body').classList.remove('no-scroll');
      } else {
        document.querySelector('body').classList.add('no-scroll');
      }
      this.showNav = !this.showNav;
    },
  },
};
</script>

<style>
.router-link-active {
  outline: none;
}

.navbar {
  position: fixed;
  width: 100%;
  display: flex;
}

.no-scroll {
  overflow: hidden;
}

</style>

<style scoped lang="scss">
.menu-button {
  cursor: pointer;
}

#app {
  display: flex;
}

header {
  height: 80px;
  display: flex;
  justify-content: space-between;

  img {
    height: 70%;
  }
}

.content {
  width: 100%;
}
</style>
