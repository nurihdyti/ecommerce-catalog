<template>
  <div class="card">
    <img :src="product.image" alt="" />
    <div class="container">
      <h4 :class="isMenProduct ? 'title-produk1' : 'title-produk'">
        <b> {{ product.title }} </b>
      </h4>
      <div class="category-rating">
        <p class="category-produk">{{ product.category }}</p>
        <div class="rating">
          <span style="margin-right: 7px">{{ product.rating.rate }}/5</span>
          <span
            :class="
              isMenProduct ? 'circles circle-blue' : 'circles circle-pink'
            "
            v-for="x in Array(Math.floor(product.rating.rate))"
            :key="x"
          ></span>
          <span
            class="circles"
            v-for="x in Array(5 - Math.floor(product.rating.rate))"
            :key="x"
          ></span>
        </div>
      </div>
      <hr class="garis" />
      <p class="detail-produk">
        {{ product.description }}
      </p>
      <hr class="garis" />
      <h4 :class="isMenProduct ? 'harga1' : 'harga'">${{ product.price }}</h4>
      <button :class="isMenProduct ? 'button-buy1' : 'button-buy'">
        Buy now
      </button>
      <button
        type="button"
        :class="isMenProduct ? 'button-next1' : 'button-next'"
        @click="onButtonClick"
      >
        Next product
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ["product"],
  methods: {
    onButtonClick() {
      this.$emit("onClickNext");
    },
  },
  computed: {
    isMenProduct() {
      return this.product.category === "men's clothing";
    },
  },
};
</script>

<style>
.category-rating,
.rating {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>