<template>
  <div id="app">
    <div class="content">
      <header class="navbar">
        <img
          src="./assets/logo.svg"
        >
        <Navigation1 v-if="!mobileView" />
        
        <div
          v-if="mobileView"
          class="menu-button"
          @click="openNav()"
        >
          <div class="menu-button_burger">
            <div class="line1" />
            <div class="line2" />
          </div>
        </div>
      </header>
      <SimpleJumbotron
        v-if="banerShow "
        class="jumb"
      />
      <div class="view">
        <router-view />
      </div>
      <Footer />
    </div>
    <NavigationMobile
      v-if="showNav"
      :item="true"
      @clicked="openNav()"
    />
  </div>
</template>

<script>
import SimpleJumbotron from '@/components/SimpleJumbotron.vue';
import Navigation1 from '@/components/Navigation1.vue';
import NavigationMobile from '@/components/NavigationMobile.vue';
import Footer from '@/components/Footer.vue';

export default {
  components: {
    SimpleJumbotron,
    Navigation1,
    NavigationMobile,
    Footer,
  },
  data() {
    return {
      mobileView: false,
      showNav: false,
      banerShow: true,
      navOnBaner: true,
      observer: null
    };
  },
  watch: {
    mobileView() {
      if (!this.mobileView) {
        this.showNav = false;
      }

      const nav = document.querySelector('.navbar');

      if (this.navOnBaner && !this.mobileView) {
          nav.style.cssText = "background: rgba(52, 58, 64, 0); box-Shadow: none; height: 100px;"
        } else {
          nav.style.cssText = "background: rgba(52, 58, 64, 1); box-Shadow: 0 1px 10px black; height: 60px;"
        }
    },
    $route() {
      this.checkUrl()
      setTimeout(() => {
        if (this.banerShow) {
          this.observer.observe(document.querySelector('.jumb'));
        } 
        window.scrollTo(0,0)
      },20)

    },
  },
  created() {
    this.observer = new IntersectionObserver(
      this.onElementObserved,
      {
        root: null,
        threshold: 0,
        rootMargin: '-100px'
      }
    );
  },
  mounted() {
    this.handleView();
    this.checkUrl();
    window.addEventListener('resize', this.handleView);

    if (this.banerShow) {
      this.observer.observe(document.querySelector('.jumb'));
    } 
  },
  methods: {
    onElementObserved(entries) {
      entries.forEach((entry) => {
        const nav = document.querySelector('.navbar');

        this.navOnBaner = entry.isIntersecting

        if (this.navOnBaner && !this.mobileView) {
          nav.style.cssText = "background: rgba(52, 58, 64, 0); box-Shadow: none; height: 100px;"
        } else {
          nav.style.cssText = "background: rgba(52, 58, 64, 1); box-Shadow: 0 1px 10px black; height: 60px;"
        }
      })
    },
    handleView() {
      this.mobileView = window.innerWidth <= 1000;
      document.querySelector('body').classList.remove('no-scroll');
    },
    openNav() {
      if (this.showNav) {
        document.querySelector('body').classList.remove('no-scroll');
        document.querySelector('.menu-button').classList.remove('openBtn');
        document.querySelector('.navigation-mobile').classList.remove('open');
        setTimeout(() => {this.showNav = !this.showNav},500);
      } else {
        this.showNav = !this.showNav;
        setTimeout(() => {
          document.querySelector('body').classList.add('no-scroll');
          document.querySelector('.menu-button').classList.add('openBtn');
          document.querySelector('.navigation-mobile').classList.add('open');
        },1);
      }
    },
    checkUrl() {
      this.banerShow = this.$route.path == '/';
    }
  },
};
</script>

<style lang="scss">
*{
  font-size: 21px;
  font-family: 'Poppins', sans-serif;
}
.router-link-active {
  outline: none;
}

.navbar {
  position: fixed;
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 1;
  transition: height 0.5s ease-in-out;
  
  img {
    height: 40%;
  }
}

.no-scroll {
  overflow: hidden;
}
@media (max-width:420px) {
  .navbar {
    img {
      width: 200px;
    }
  }
}

@media (max-width:1000px) {
  *{
    font-size: 16px;
  }

  .navbar {
    height: 50px;

    img {
      height: 70%;
    }
  }
}

// Menu Button

.menu-button {
  height: 30px;
  width: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: all .5s ease-in-out;

  .menu-button_burger {
    display: flex;
    flex-direction: column;
    width:  30px;
    height: 4px;
    transition: all .5s ease-in-out;

    .line1,
    .line2 {
      width: 30px;
      height: 4px;
      background: crimson;
      margin: 0;
      padding: 0;
      position: absolute;
      transition: all .5s ease-in-out;
    }
  }

  .menu-button_burger::before,
  .menu-button_burger::after {
    content: '';
    position: absolute;
    width:  30px;
    height: 4px;
    background: crimson;
    transition: all .5s ease-in-out;
    margin: 0;
    padding: 0;
  }

  .menu-button_burger::before {
    transform: translateY(-10px);
  }

  .menu-button_burger::after {
    transform: translateY(10px);
  }
}

.menu-button.openBtn {
  .line1 {
    transform: rotate(45deg);
  }
  .line2 {
    transform: rotate(-45deg);
  }

  .menu-button_burger::before {
    transform: translateY(0px);
    background: transparent;
    height: 0;
  }

  .menu-button_burger::after {
    transform: translateY(0px);
    background: transparent;
    height: 0;
  }
}
</style>

<style scoped lang="scss">
.menu-button {
  cursor: pointer;
}

#app {
  display: flex;
}

.content {
  width: 100%;
}

.view {
  max-width: 1200px;
  margin: auto;
}
</style>
