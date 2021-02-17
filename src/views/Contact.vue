<template>
  <div class="contact">
    <h1>Kontakt</h1>

    <div class="bus-card">
      <img
        alt="akcenty logo"
        src="../assets/logo.svg"
      >
      <div class="line" />

      <div class="info">
        <div class="up">
          <b>Sebastian Szymański</b><br>
          tel.kom. 513 091 914
        </div>
        <div class="bottom">
          Pracownia Projektowa<br>
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
      </div>
      <img
        alt="Vue logo"
        src="../assets/logo.png"
      >
    </div>
  </div>
</template>
<style scoped lang="scss">
  div {
    display: flex;
  }

  .bus-card {
    width: 100%;
    height: 40%;
    background-color: lightgray;
    flex-direction: row;
    justify-content: space-around;
    padding: 50px 20px 20px 20px;
    margin: 100px 0 100px 0;

    img {
      width: 250px;
      height: 20%;
      padding-top: 20px;
    }

    .line {
      background-color: orange;
      width: 5px;
      height: 110px;
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

  @media (max-width: 500px) {
    .bus-card {
      width: 90vw;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      margin-top: 60px;

      img {
        width: 80%;
      }

      .info {
        align-items: center;
        justify-content: center;
        width: 100%;
        padding: 0;

        .bottom {
          margin-top: 0;
        }
      }

      .line {
        height: 5px;
        width: 90%;
        margin: 30px 0 30px 0;
      }
    }

    .contact {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 150px 20px 100px 20px;
    }

    .row {
      img {
        padding-top: 100px;
      }
    }
  }
</style>
