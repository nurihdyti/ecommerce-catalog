<template>
  <div class="card">
    <img :src="product.image" alt="" width="80%" />
    <div class="container">
      <h4 class="title-produk1">
        <b> {{ product.title }} </b>
      </h4>
      <p class="category-produk">{{ product.category }}</p>
      <hr class="garis" />
      <p class="detail-produk">
        {{ product.description }}
      </p>
      <hr class="garis" />
      <h4 class="harga1">${{ product.price }}</h4>
      <button class="button-buy1">Buy now</button>
      <button type="button" class="button-next1" @click="onButtonClick">
        Next product
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "MenProduct",
  props: ["product"],
  methods: {
    onButtonClick() {
      this.$emit("onClickNext");
    },
  },
};
</script>