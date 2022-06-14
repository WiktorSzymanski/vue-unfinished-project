<template>
  <div class="contact">
    <div class="panel">
      <h1>Kontakt</h1>

      <div class="bus-card">
        <img
          alt="Vue logo"
          src="../assets/logo.png"
        >

        <div class="info">
          <div class="up">
            <b>Sebastian Szymański</b><br>
            tel.kom. 513 091 914
          </div>
          <div class="bottom">
            <b>Pracownia Projektowa</b>
            os. Stefana Batorego 36<br>
            60-687 Poznań<br>
            e-mail: akcenty@wp.pl
          </div>
        </div>
      </div>
    </div>
    <div class="back-ground" :style="position"/>
    <div 
      id="4"
      class="wholeForm" 
    >
      <h1>Napisz do nas</h1>
      <div class="formWimg">
        <div class="form">
          <span>Imie i Nazwisko</span>
          <input type="text" size="1">
          <span>E-mail</span>
          <input type="text">
          <span>Temat</span>
          <input type="text">
        </div>
        <div class="imgCon">
          <img
            alt="Vue logo"
            src="../assets/logo.png"
          >
        </div>
      </div>
      <span class="wiad">Wiadomość</span>
      <textarea />
      <div class="buttons">
        <button
          class="clear"
          @click="clear()"
        >
          Clear
        </button>
        <button class="submit">
          Submit
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      position: null,
      panels: {
        panel: {
          pointer: '.panel',
          isVisible: false,
          listener: null
        },
        wholeForm: {
          pointer: '.wholeForm',
          isVisible: false,
          listener: null
        }
      }
    };
  },
  mounted() {
    var element = this.panels['panel'];
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

      this.setBackgroundPosition();
    },20);

    setInterval(this.setBackgroundPosition, 0.5);
  },
  methods: {
    setBackgroundPosition () {
      let wraper = document.getElementById('4');
      let bound = wraper.getBoundingClientRect();

      console.log(bound);

      this.position = `top: ${bound.top}px; height: ${bound.height}px`
    },
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
    clear() {
      document.querySelectorAll("input").value = '';
      document.querySelector("textarea").value = '';
    }
  },
}
</script>

<style scoped lang="scss">
  div {
    display: flex;
  }

  .seen {
    transform: translateX(0px) !important;
    opacity: 1 !important;
  }
  
  .panel {
    transition: all 0.5s ease-out;
    transform: translateX(50px);
    opacity: 0;
    margin-bottom: 100px;
  }

  .bus-card {
    width: 100%;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    padding: 0 20px 0 20px;

    img {
      max-height: 200px;
    }

    .info {
      min-height: 300px;
      text-align: justify;
      flex-direction: column;
      display: flex;
      padding: 20px 0 20px 0;

      .up {
        display: block;
      }

      .bottom {
        display: flex;
        flex-direction: column;
        margin-top: auto;
        padding-bottom: 10px;
      }
    }
  }

  .wholeForm {
    color: white;
    width: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 100px 20px 100px 20px;

    transition: all 0.5s ease-out;
    transform: translateX(50px);
    opacity: 0;

    .formWimg {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;

      .imgCon {
        width: 50%;
        justify-content: center;

        img {
          max-height: 200px;
        }
      }
    }

    h1 {
      margin-bottom: 30px;
    }

    input {
      border-top: none;
      // border-bottom-color: darkgrey;
      background-color: white;
      // border-right-color: darkgrey;
      border-left: none;
      margin-bottom: 10px;
      // border-radius: 10px;
      padding: 5px 10px 5px 10px;
      width: 100%;
    }

    input:focus{
      outline: none;
    }

    .wiad {
      width: 100%;
    }

    textarea {
      // border-color: darkgrey;
      border-width: 2px;
      background-color: white;
      // border-radius: 10px;
      border-top: none;
      // border-right-color: darkgrey;
      border-left: none;
      padding: 5px 10px 5px 10px;
      resize: none;
      width: 100%;
      height: 200px;
    }

    textarea:focus {
      outline: none;
    }

    .buttons {
      display: flex;
      width: 100%;
      justify-content: space-between;
      margin-top:20px;

      button {
        width: 48%;
        border-color: darkgrey;
        border-width: 2px;
        background: rgba(52, 58, 64);
        // border-radius: 10px;
        border-top: none;
        border-right-color: darkgrey;
        border-left: none;
        color: white;
        font-weight: 700;
      }

      button:focus {
        outline: none;
      }
    }
  }

  .contact {
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    min-height: 100vh;
    padding: 200px 10px 100px 10px;
    overflow-x: hidden;
  }

  .panel {
    padding-top: 100px;
    padding-bottom: 50px;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 70vh;
  }
  
  .form {
    display: flex;
    flex-direction: column;
    min-width: 50%;
  }

  h1 {
    font-family: 'Poppins';
  }

  span {
    font-family: 'Roboto', sans-serif;
  }

  @media (max-width: 580px) {
    .panel {
      height: auto;
    }
    .bus-card {
      width: 90vw;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      margin-top: 60px;
      padding: 0;

      .info {
        justify-content: center;
        padding: 0;
        .up {
          font-size: 20px;

          b {
            font-size: 20px;
          }
        }
        .bottom {
          margin-top: 20px;
          font-size: 20px;
          b {
            font-size: 20px;
          }
        }
      }

      img {
        width: 70%;
        margin-left: auto;
        margin-right: auto;
        padding-bottom: 50px;
        max-height: unset;
      }
    }

    .contact {
      display: flex;
      width: 100%;
      flex-direction: column;
      align-items: center;
      padding: 150px 20px 100px 20px;
    }

    .wholeForm {
      .imgCon {
        display: none;
      }
      .form {
        width: 100%;
        min-width: unset;
      }
    }
  }

  .back-ground {
    position: fixed;
    width: 100vw;
    background: gray;
    top: 0;
    left: 0;
  }
</style>
