<template>
  <div>
    <div
      class="jumbotron jumbotron-fluid d-none d-lg-block jumbotron-img"
      :style="{ backgroundImage: `url('${imgUrl}'` }"
    />
  </div>
</template>

<script>
const imgUrls = [
  'https://images.unsplash.com/photo-1470790376778-a9fbc86d70e2',
  'https://images.unsplash.com/photo-1546146477-15a587cd3fcb?ixlib=rb-1.2.1&auto=format&fit=crop&w=564&q=80',
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
    }, 2000);
  },
};
</script>

<style scoped>
.jumbotron {
  margin-bottom: 0;
  min-height: 50vh;
}
.jumbotron-img {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
