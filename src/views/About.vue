<template>
  <div class="about">
    <div id="panel">
      <img
        alt="Vue logo"
        src="../assets/logo.png"
      >
      <div id="panel-concent">
        <h1>O Nas</h1>
        <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
          Mauris aliquet consequat finibus.
          Donec augue nunc, vehicula non diam eget, tempor interdum magna.
          Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
          Sed ullamcorper nibh a scelerisque dictum.
          Vivamus posuere pharetra arcu vitae mattis.</span>
      </div>
    </div>

    <!-- <div id="panel">
      <div id="panel-concent">
        <h1>Dlaczego my?</h1>
        <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
          Mauris aliquet consequat finibus.
        Donec augue nunc, vehicula non diam eget, tempor interdum magna.
        Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
        Sed ullamcorper nibh a scelerisque dictum.
        Vivamus posuere pharetra arcu vitae mattis.</span>
      </div>
      <img alt="Vue logo" src="../assets/logo.png">
    </div> -->
  </div>
</template>
<style scoped>
  div {
    display: flex;
  }

  .about {
    flex-direction: column;
    justify-content: space-around;
    padding: 100px 10px 100px 10px;
    min-height: 70vh;
  }

  #panel {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }
  #panel-concent {
    display: flex;
    flex-direction: column;
    max-width: 600px;
    flex-wrap: wrap;
  }

  img {
    margin-top:5%
  }

  #panel-concent h1 {
    align-self: flex-start;
    text-indent: 1vw;
  }

  h1 {
    font-family: 'Poppins';
  }

  span {
    font-family: 'Roboto', sans-serif;
  }
</style>
