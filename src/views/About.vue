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
<style scoped lang="scss">
  div {
    display: flex;
  }

  .about {
    flex-direction: column;
    justify-content: space-around;
    min-height: 100vh;
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
