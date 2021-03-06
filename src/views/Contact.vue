<template>
  <div class="contact">
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

    <div class="row">
      <div class="info">
        <h1>Napisz do nas</h1>
        <span>Imie i Nazwisko</span>
        <input type="text">
        <span>E-mail</span>
        <input type="text">
        <span>Temat</span>
        <input type="text">
        <span>Wiadomość</span>
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
      <img
        alt="Vue logo"
        src="../assets/logo.png"
      >
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    clear() {
      document.querySelectorAll("input").value = '';
      document.querySelector("textarea").value = '';
    }
  }
}
</script>

<style scoped lang="scss">
  div {
    display: flex;
  }

  .bus-card {
    width: 100%;
    height: 40%;
    flex-direction: row;
    justify-content: space-around;
    padding: 50px 20px 20px 20px;
    margin: 100px 0 100px 0;

    img {
      width: 250px;
      height: 20%;
      padding-top: 20px;
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

  .row {
    width: 100%;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;

    h1 {
      margin-bottom: 30px;
    }

    input {
      border-top: none;
      border-bottom-color: darkgrey;
      background-color: rgb(235, 235, 235);
      border-right-color: darkgrey;
      border-left: none;
      margin-bottom: 10px;
      border-radius: 10px;
      padding: 5px 10px 5px 10px;
    }

    input:focus{
      outline: none;
    }

    textarea {
      border-color: darkgrey;
      border-width: 2px;
      background-color: rgb(235, 235, 235);
      border-radius: 10px;
      border-top: none;
      border-right-color: darkgrey;
      border-left: none;
      padding: 5px 10px 5px 10px;
      resize: none;
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
        border-radius: 10px;
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
  }

  .panel {
    flex-direction: column;
    align-items: center;
    margin-top: 100px;
    margin-bottom: 100px;
  }

  .panel h1 {
    margin-bottom: 100px;
  }

  .info {
    display: flex;
    flex-direction: column;
    max-width: 600px;
  }

  #panel-content h1 {
    align-self: flex-start;
  }

  #panel-content input{
    width: 100%;
  }

  h1 {
    font-family: 'Poppins';
  }

  span {
    font-family: 'Roboto', sans-serif;
  }

  @media (max-width: 600px) {
    .bus-card {
      width: 90vw;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      margin-top: 60px;

      .info {
        align-items: center;
        justify-content: center;
        width: 100%;
        padding: 0;

        .bottom {
          margin-top: 0;
        }
      }
    }

    .contact {
      display: flex;
      width: 100%;
      flex-direction: column;
      align-items: center;
      padding: 150px 20px 100px 20px;
    }

    .row {
      flex-direction: column;

      img {
        padding-top: 100px;
      }
    }
  }
</style>
