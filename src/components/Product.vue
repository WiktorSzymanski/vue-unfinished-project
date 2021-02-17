<template>
  <div 
    class="product"
    :class="{'opened':open}"
    @click="openDesc()"
  >
    <img
      alt="Vue logo"
      :src="item.img"
    >
    <div class="description">
      <h4>
        {{ item.name }}
      </h4>
      <p class="desc">
        {{ open ? item.long : item.short }}
      </p>
      <p class="price">
        Cena: {{ item.price }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object,
            default: null
        }
    },
    data() {
      return {
        open: false
      }
    },
    methods: {
      openDesc() {
        this.open = !this.open
      }
    }
}
</script>

<style scoped lang="scss">
.opened {
  min-height: 500px;
}

.product {
    background: lightgray;
    width: 100%;
    margin-top: 50px;
    flex-direction: row;
    display: flex;
    padding: 20px;
    min-height: 250px;

    img {
      padding-right: 20px;
      min-height: 210px;
    }

    .description {
      min-height: 100%;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;

      .price {
        margin-top: auto;
      }
    }
  }

  @media (max-width: 500px) {
    .product {
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 10px;

      img {
        width: 100%;
        padding: 0;
      }

      .description {
        flex-direction: row;
        .desc {
          display: none;
        }
      }
    }
  }
</style>