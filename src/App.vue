<template>
  <div id="app">
    <div class="content">
      <header class="navbar">
        <img
          src="./assets/logo.svg"
          :class="{'half-height' : mobileView}"
        >
        <Navigation1 v-if="!mobileView" />
        <!-- <div /> -->
        
        <img
          v-if="mobileView"
          class="menu-button"
          :src="menuButton"
          @click="openNav()"
        >
      </header>
      <SimpleJumbotron
        v-if="!mobileView && banerShow "
      />
      <!-- <Navigation2 v-if="!mobileView" /> -->
      <div class="view">
        <router-view />
      </div>
      <Footer />
    </div>
    <NavigationMobile
      v-if="showNav"
      @clicked="openNav()"
    />
  </div>
</template>

<script>
import SimpleJumbotron from '@/components/SimpleJumbotron.vue';
import Navigation1 from '@/components/Navigation1.vue';
// import Navigation2 from '@/components/Navigation2.vue';
import NavigationMobile from '@/components/NavigationMobile.vue';
import Footer from '@/components/Footer.vue';
import { bus } from './main';

export default {
  components: {
    SimpleJumbotron,
    Navigation1,
    // Navigation2,
    NavigationMobile,
    Footer,
  },
  data() {
    return {
      mobileView: false,
      showNav: false,
      banerShow: true,
      menuButton: '/logo-short.svg',
    };
  },
  watch: {
    mobileView() {
      if (!this.mobileView) {
        this.showNav = false;
      }
    },
    $route() {
      this.checkUrl()
      setTimeout(() => {
        window.scrollTo(0,0)
      },20)
    }
  },
  mounted() {
    this.handleView();
    this.checkUrl();
    window.addEventListener('resize', this.handleView);
  },
  methods: {
    handleView() {
      this.mobileView = window.innerWidth <= 930;
      bus.$emit('mobileView',this.mobileView);
      document.querySelector('body').classList.remove('no-scroll');
    },
    openNav() {
      if (this.showNav) {
        document.querySelector('body').classList.remove('no-scroll');
      } else {
        document.querySelector('body').classList.add('no-scroll');
      }
      this.showNav = !this.showNav;

      if (this.menuButton == '/logo-short.svg') {
        this.menuButton = '/logo-short-x.svg'
      } else {
        this.menuButton = '/logo-short.svg'
      }
    },
    checkUrl() {
      this.banerShow = this.$route.path == '/';
    }
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
  background: rgba(52, 58, 64, 1);
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
  align-items: center;
  box-shadow: 0 1px 10px black;
  
  img {
    height: 50%;
  }
}

.content {
  width: 100%;
}

.half-height {
  height: 25%;
}

.view {
  max-width: 1000px;
  margin: 0 auto 0 auto;
}
</style>
