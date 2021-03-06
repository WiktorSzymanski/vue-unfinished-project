<template>
  <div id="app">
    <div class="content">
      <header class="navbar">
        <img
          src="./assets/logo.svg"
        >
        <Navigation1 v-if="!mobileView" />
        <!-- <div /> -->
        
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
      <!-- <Navigation2 v-if="!mobileView" /> -->
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
// import Navigation2 from '@/components/Navigation2.vue';
import NavigationMobile from '@/components/NavigationMobile.vue';
import Footer from '@/components/Footer.vue';
// import { bus } from './main';

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
    },
  },
  mounted() {
    this.handleView();
    this.checkUrl();
    window.addEventListener('resize', this.handleView);


    //----------------------------------------------
    if (this.mobileView) {
      document.querySelector('.navbar').style.background = 'rgba(52, 58, 64, 1)';
      document.querySelector('.navbar').style.boxShadow = '0 1px 10px black';
    }
    document.addEventListener("scroll",this.navbarOpacity());
  },
  methods: {
    //-----------------------------------------------------------
    navbarPosition() {
      const rect = document.querySelector('.jumb').getBoundingClientRect();

      return (
        ((rect.bottom - 100)/window.innerHeight) > 0
      );
    },
    navbarOpacity() {
      return () => {
        console.log(this.navbarPosition());
        const nav = document.querySelector('.navbar');
        if (this.navbarPosition() && !this.mobileView) {
          nav.style.background = 'rgba(52, 58, 64, 0)';
          nav.style.boxShadow = 'none';
          nav.style.height = '100px';
        } else {
          nav.style.background = 'rgba(52, 58, 64, 1)';
          nav.style.boxShadow = '0 1px 10px black';
          nav.style.height = '60px';
        }
      }
    },








    //-----------------------------------------------------------

    handleView() {
      this.mobileView = window.innerWidth <= 1000;
      // bus.$emit('mobileView',this.mobileView);
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
  // background: rgba(52, 58, 64, 1);
  // box-shadow: 0 1px 10px black;
  z-index: 1;
  transition: height 0.5s ease-in-out;
  
  img {
    height: 40%;
  }
}

.no-scroll {
  overflow: hidden;
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
