<template>
  <div class="about">
    <div class="panel">
      <img
        alt="Vue logo"
        src="../assets/logo.png"
      >
      <div class="panel-concent">
        <h1>O Nas</h1>
        <span>Działamy na rynku od 1996 roku i cieszymy się zasłużoną renomą wysokiej jakości usług z zakresu: wystawiennictwa, architektury wnętrz,
          informacji wizualnej, architektury zieleni. Nie obawiamy się nowych wyzwań i technologii, doskonale orientujemy się w aktualnych trendach
          czerpiąc z nich to, co najlepsze i mamy ciągle nowe pomysły. Nie podejmujemy decyzji bez zastanowienia oraz szanujemy doświadczenia i zdanie
          innych.</span>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  name: "About",
  data() {
    return {
      panels: {
        about: {
          pointer: '.about',
          isVisible: false,
          listener: null
        },
      }
    };
  },
  mounted() {
    var element = this.panels['about'];
    element.isVisible = true;
    for (const key of Object.keys(this.panels)) {
      console.log(key);
      this.panels[key].pointer = document.querySelector(this.panels[key].pointer);
      this.panels[key].listener = this.triggerIsInViewport(this.panels[key]);
      document.addEventListener("scroll",this.panels[key].listener);
    }
    setTimeout(() => {
      if (element.isVisible) {
        element.pointer.classList.add("seen");
        document.removeEventListener("scroll", element.listener);
      }
    },20);
  },
  methods: {
    isInViewport(element) {
      const rect = element.getBoundingClientRect();

      return (
        rect.top <= window.innerHeight * 2
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

  .about {
    flex-direction: column;
    justify-content: space-around;
    min-height: 100vh;

    transition: all 0.5s ease-out;
    transform: translateX(50px);
    opacity: 0;
  }

  .seen {
    transform: translateX(0px);
    opacity: 1;
  }

  .panel {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding: 0 40px 0 40px;
  }
  .panel-concent {
    display: flex;
    flex-direction: column;
    max-width: 60%;
    flex-wrap: wrap;

    h1 {
      align-self: flex-start;
      font-family: 'Poppins';
    }
  }

  img {
    width: 30%;
  }

  span {
    font-family: 'Roboto', sans-serif;
    text-align: justify;
  }

  @media (max-width: 800px) {
    .panel {
      padding: 0 40px 0 40px;
      .panel-concent {
        max-width: 40%;
      }
      img {
        width: 50%;
      }
    }
  }

  @media (max-width: 580px) {
    .panel {
      padding: 150px 40px 100px 40px;
      .panel-concent {
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
