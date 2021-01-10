<template>
  <div class="home">
    <div class="greetings panel">
      <h1>Coś Tam</h1>
      <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
          Mauris aliquet consequat finibus.
        Donec augue nunc, vehicula non diam eget, tempor interdum magna.
        Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
        Sed ullamcorper nibh a scelerisque dictum.
        Vivamus posuere pharetra arcu vitae mattis.</span>
    </div>

    <div class="mid panel">
      <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
          Mauris aliquet consequat finibus.
        Donec augue nunc, vehicula non diam eget, tempor interdum magna.
        Nam sed nulla rutrum, tincidunt augue vel, maximus odio.
        Sed ullamcorper nibh a scelerisque dictum.
        Vivamus posuere pharetra arcu vitae mattis.</span>
      <img alt="Vue logo" src="../assets/logo.png">
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

export default {
  name: 'Home',
};
</script>

<style scoped>
  div {
    display: flex;
  }

  .home {
    flex-direction: column;
    justify-content: space-around;
    min-height: 100vh;
    padding: 100px 10px 100px 10px;
  }

  .panel {
    margin-top: 100px;
    margin-bottom: 100px;
  }

  .greetings {
    flex-direction: column;
    text-align: center;
  }

  .mid span {
    max-width: 600px;
  }

  .mid{
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .gallery {
    flex-direction: column;
  }

  .slide-show {
    width: 100%;
    background: #343a40;
    align-items: center;
    justify-content: center;
  }

  .gallery span {
    margin-top: 50px;
    text-align: center;
  }
</style>
