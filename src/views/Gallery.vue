<template>
  <div class="gallery">
    <div
      v-if="imageShown"
      class="big_image"
    > 
      <div class="im_area">
        <img
          :src="imageShownData.img"
          :alt="imageShownData.name"
        >
        <img
          src="/logo-short-x.svg"
          class="close"
          style="color:white;"
          @click="closeImage()"
        >
      </div>
    </div>
    <h1>Galeria</h1>
    <div class="images">
      <img
        v-for="(item, index) of images"
        :key="index"
        class="imag"
        :src="item.img"
        :alt="item.name"
        @click="showImage(item)"
      >
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        images: [],
        imageShown: false,
        imageShownData: []
      }
    },
    mounted() {
      let req = new XMLHttpRequest();

      req.open('GET', '/text.json', false);
      req.send(null);

      if (req.status == 200) {
        this.images = JSON.parse(req.responseText).images
      }
    },
    methods: {
      showImage(item) {
        this.imageShownData = item;
        this.imageShown = true;
        document.querySelector('body').classList.add('no-scroll');
      },
      closeImage() {
        this.imageShown = false;
        document.querySelector('body').classList.remove('no-scroll');
      }
    }
  }
</script>

<style scoped lang="scss">

  .gallery {
    padding: 150px 20px 20px 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .images {
    width: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;

    .imag {
      width: 32%;
      margin-bottom: 2%;
      object-fit: cover;
      cursor: pointer;
    }
  }

  .big_image {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    height: 100%;
    width: 100%;
    padding: 50px;
    background: rgba(52, 58, 64, 0.95);
    bottom: 0;

    .im_area {
      display: flex;
      align-items: center;
      justify-content: center;
    }

    img {
      width: 50vw;
    }

    .close {
      cursor: pointer;
      align-self: flex-start;
      width: 30px;
      position: relative;
      top: 2px;
      margin: 0 0 0 -28px;
    }
  }

  @media (max-width: 600px) {
    .images {
      .imag {
        width: 49%;
        margin-bottom: 2%;
      }
    }
  }

  @media (max-width: 1000px) {
    .big_image {
      img {
        width: 90vw;
      }
    }
  }
</style>