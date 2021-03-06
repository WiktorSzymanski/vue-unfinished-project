<template>
  <div class="home">
    <div class="greetings panel">
      <h1>Coś Tam</h1>
      <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquet
        consequat finibus. Donec augue nunc, vehicula non diam eget, tempor
        interdum magna. Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
        Sed ullamcorper nibh a scelerisque dictum. Vivamus posuere pharetra arcu
        vitae mattis.</span>
    </div>

    <div class="mid panel">
      <img
        alt="Vue logo"
        src="../assets/logo.png"
      >
      <!-- :class="{'mobile-img' : mobileView}" -->
      <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris aliquet
        consequat finibus. Donec augue nunc, vehicula non diam eget, tempor
        interdum magna. Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
        Sed ullamcorper nibh a scelerisque dictum. Vivamus posuere pharetra arcu
        vitae mattis.</span>
    </div>

    <!-- <div class="gallery panel">
      <div class="slide-show">
        <img alt="Vue logo" src="../assets/logo.png">
      </div>
      <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      Mauris aliquet consequat finibus.
      Donec augue nunc, vehicula non diam eget, tempor interdum magna.
      Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
      Sed ullamcorper nibh a scelerisque dictum.
      Vivamus posuere pharetra arcu vitae mattis.</span>
    </div> -->
  </div>
</template>

<script>
// import { bus } from '../main';

export default {
  name: "Home",
  data() {
    return {
      panels: {
        greet: {
          pointer: '.greetings',
          isVisible: false,
          listener: null
        },
        mid: {
          pointer: '.mid',
          isVisible: false,
          listener: null
        }
      }
    };
  },
  mounted() {
    for (const key of Object.keys(this.panels)) {
      this.panels[key].pointer = document.querySelector(this.panels[key].pointer);
      this.panels[key].listener = this.triggerIsInViewport(this.panels[key]);
      document.addEventListener("scroll",this.panels[key].listener);
    }
  },
  methods: {
    isInViewport(element) {
      const rect = element.getBoundingClientRect();

      return (
        rect.top <= window.innerHeight * 0.75
      );
    },
    triggerIsInViewport(element) {
      return () => {
        element.isVisible = this.isInViewport(element.pointer);

        if (element.isVisible) {
          element.pointer.classList.add("seen");
          document.removeEventListener("scroll", element.listener);
        }
      };
    },
  },
};
</script>

<style scoped lang="scss">
div {
  display: flex;
}

.home {
  flex-direction: column;
  justify-content: space-around;
  padding-top: 100px;
  padding-bottom: 100px;
  overflow-x: hidden;
}

.panel {
  padding: 100px 40px 100px 40px;
}

.greetings {
  flex-direction: column;
  text-align: justify;
  position: relative;

  transition: all 0.5s ease-out;
  transform: translateX(20px);
  opacity: 0;

  h1 {
    text-align: center;
    padding-bottom: 20px;
  }
}

.mid {
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  text-align: justify;

  transition: all 0.5s ease-out;
  transform: translateX(-20px);
  opacity: 0;

  span {
    max-width: 60%;
  }

  img {
    width: 30%;
  }
}

.seen {
  transform: translateX(0px);
  opacity: 1;
}

// .gallery {
//   flex-direction: column;

//   span {
//     margin-top: 50px;
//     text-align: center;
//   }
// }

// .slide-show {
//   width: 100%;
//   background: #343a40;
//   align-items: center;
//   justify-content: center;
// }

@media (max-width: 800px) {
  .panel {
    padding: 50px 40px 50px 40px;
  }

  .mid {
    span {
      max-width: 40%;
    }
    img {
      width: 50%;
    }
  }
}

@media (max-width: 580px) {
  .panel {
    padding: 40px 20px 40px 20px;
  }

  .greetings {
    span {
      width: 100%;
    }
  }

  .mid {
    span {
      max-width: 100%;
    }
    img {
      width: 80%;
      margin-left: auto;
      margin-right: auto;
      padding-bottom: 50px;
    }
  }
}
</style>
