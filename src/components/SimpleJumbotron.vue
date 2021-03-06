<template>
  <div>
    <div
      class="jumbotron jumbotron-fluid jumbotron-img"
      :style="{ backgroundImage: `url('${imgUrl}'` }"
    />
  </div>
</template>

<script>
const imgUrls = [
  'simpleJumb/image001.jpg',
  'simpleJumb/image004.jpg',
];

export default {
  name: 'SimpleJumbotron',
  data() {
    return {
      count: 0,
    };
  },
  computed: {
    imgUrl() {
      return imgUrls[this.count % imgUrls.length];
    },
  },
  created() {
    setInterval(() => {
      this.count += 1;
    }, 3000);
  },
};
</script>

<style scoped>
.jumbotron {
  margin-bottom: 0;
  height: 100vh;
}
.jumbotron-img {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  transition: all 1s ease-in-out;
  object-fit: cover;
}
</style>
