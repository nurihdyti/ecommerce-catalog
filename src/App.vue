<template>
  <div id="app" :style="bgColor">
    <LoadingCard v-if="isLoading"></LoadingCard>
    <template v-else>
      <CardProduct :product="product" @onClickNext="getProducts" v-if="product">
      </CardProduct>
      <NoProduct v-else @onClickNext="getProducts" />
    </template>
    <div id="background-bawah"></div>
  </div>
</template>

<script>
import CardProduct from "./components/CardProduct.vue";
import NoProduct from "./components/NoProduct.vue";
import LoadingCard from "./components/LoadingCard.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    CardProduct,
    NoProduct,
    LoadingCard,
  },
  data() {
    return {
      product: null,
      id_product: 1,
      isLoading: false,
    };
  },
  methods: {
    getProducts() {
      this.isLoading = true;
      axios
        .get("https://fakestoreapi.com/products/" + this.id_product.toString())
        .then((value) => {
          if (
            value.data.category === "women's clothing" ||
            value.data.category === "men's clothing"
          ) {
            this.product = value.data;
          } else {
            this.product = null;
          }
          this.isLoading = false;

          if (this.id_product === 20) {
            this.id_product = 1;
          } else {
            this.id_product = this.id_product + 1;
          }
        });
    },
  },
  computed: {
    bgColor() {
      if (this.product?.category === "men's clothing") {
        return { "--background-color": "#d6e6ff" };
      } else if (this.product?.category === "women's clothing") {
        return { "--background-color": "#FDE2FF" };
      } else {
        return { "--background-color": "#dcdcdc" };
      }
    },
  },
  mounted() {
    this.getProducts();
  },
};
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;
  background-color: var(--background-color);
  display: flex;

  justify-content: center;
  align-items: center;
  background-image: url("./assets/bg-pattern.png");
}

body {
  margin: 0;
}

#background-blue {
  background-color: #d6e6ff;
}

#background-gray {
  background-color: #dcdcdc;
  background-image: none;
}

#background-bawah {
  position: fixed;
  height: 35vh;
  width: 100%;
  background-color: white;
  bottom: 0;
  left: 0;
}

.card {
  width: 80%;
  height: 70vh;
  display: flex;
  padding-left: 32px;
  padding-right: 32px;
  padding-top: 48px;
  padding-bottom: 48px;
  margin: auto;
  border-radius: 10px;
  background: #fff;
  box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
  z-index: 2;
}

.container {
  padding: 2px 16px;
}

.center {
  display: flex;
  width: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-image: url(./assets/sad-face.png);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: 65px 65px;
}

.title-produk {
  color: #720060;
  font-family: Inter;
  font-size: 28px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
}

.title-produk1 {
  color: #002772;
  font-family: Inter;
  font-size: 28px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
}

.category-produk {
  color: #3f3f3f;
  font-family: Inter;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.rating {
  color: #3f3f3f;
  font-family: Inter;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.circles {
  height: 15px;
  width: 15px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
}

.circle-blue {
  background-color: #002772;
}

.circle-pink {
  background-color: #720060;
}

.garis {
  stroke-width: 1px;
  stroke: rgba(0, 0, 0, 0.2);
}

.detail-produk {
  color: #1e1e1e;
  font-family: Inter;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.harga {
  color: #720060;
  font-family: Inter;
  font-size: 28px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
}

.button-buy {
  width: 259px;
  height: 42px;
  flex-shrink: 0;
  color: #fff;
  font-family: Inter;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 4px;
  background: #720060;
}

.button-next {
  width: 259px;
  height: 42px;
  flex-shrink: 0;
  color: #720060;
  font-family: Inter;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 4px;
  border: 3px solid #720060;
  background: #fff;
}

.harga1 {
  color: #002772;
  font-family: Inter;
  font-size: 28px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
}

.button-buy1 {
  width: 259px;
  height: 42px;
  flex-shrink: 0;
  color: #fff;
  font-family: Inter;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 4px;
  background: #002772;
}

.button-next1 {
  width: 259px;
  height: 42px;
  flex-shrink: 0;
  color: #002772;
  font-family: Inter;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 4px;
  border: 3px solid #002772;
  background: #fff;
}

.button-next2 {
  width: 259px;
  height: 42px;
  flex-shrink: 0;
  color: #3f3f3f;
  font-family: Inter;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 4px;
  border: 3px solid #3f3f3f;
  background: #fff;
}
</style>
