<template>
  <div class="contact">
    <div class="panel">
      <h1>Kontakt</h1>

      <div class="bus-card">
        <img alt="Vue logo" src="../assets/logo.png">
        <div class="info">
          <span>Sebastian Szymański</span>
          <span>tel.: 513 091 914</span>
          <span>e-mail: akcenty@wp.pl</span>
          <span>Pracownia Projektowa</span>
          <span>os. Stefana Batorego 36</span>
          <span>60-687 Poznań</span>
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
        <textarea></textarea>
      </div>
      <img alt="Vue logo" src="../assets/logo.png">
    </div>
  </div>
</template>
<style scoped>
  div {
    display: flex;
  }

  .bus-card {
    width: 100%;
    height: 400px;
    background-color: lightgray;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
  }

  .row {
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
  }

  .contact {
    flex-direction: column;
    justify-content: space-around;
    min-height: 100vh;
    padding: 100px 10px 100px 10px;
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

  img {
    margin-top:5%
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
</style>
