<template>
  <div class="gallery">
    <h1>Gallery</h1>
    <div class="panel">
      <div class="images">
          <a href="..\assets\gallery\1.jpg" class="img-1">
          </a>
          <a href="..\assets\gallery\2.jpg" class="img-2">
          </a>
          <a href="..\assets\gallery\3.jpg" class="img-3">
          </a>
          <a href="..\assets\gallery\4.jpg" class="img-4">
          </a>
          <a href="..\assets\gallery\5.jpg" class="img-5">
          </a>
          <a href="..\assets\gallery\6.jpg" class="img-6">
          </a>
          <a href="..\assets\gallery\7.jpg" class="img-7">
          </a>
          <a href="..\assets\gallery\8.jpg" class="img-8">
          </a>
      </div>
    </div>
  </div>
</template>

<style scoped>

  .panel {
    margin-top: 100px;
    margin-bottom: 100px;
  }


  h1 {
    margin-bottom: 100px;
    margin-left: 42%;
  }

  .gallery {
    min-height: 100vh;
    padding: 100px 10px 100px 10px;
  }


  .images {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: auto;
    grid-gap: 20px;
    grid-template-areas:
                    'img-1 img-2 img-3 img-3'
                    'img-1 img-4 img-5 img-6'
                    'img-7 img-7 img-8 img-6';
  }

  .img-1{
    grid-area: img-1;
    background-image: url('../assets/gallery/1.jpg');
    min-height: 820px;
  }

  .img-2{
    grid-area: img-2;
    background-image: url("../assets/gallery/2.jpg");
  }
.img-3{
    grid-area: img-3;
    background-image: url("../assets/gallery/3.jpg");
  }

  .img-4{
    grid-area: img-4;
    background-image: url("../assets/gallery/4.jpg");
  }

  .img-5{
    grid-area: img-5;
    background-image: url("../assets/gallery/5.jpg");
  }

  .img-6{
    grid-area: img-6;
    background-image: url("../assets/gallery/6.jpg");
    min-height: 820px;
  }

  .img-7{
    grid-area: img-7;
    background-image: url("../assets/gallery/7.jpg");
  }

  .img-8{
    grid-area: img-8;
    background-image: url("../assets/gallery/8.jpg");
  }

  </style>
