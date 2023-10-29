<template>
  <div class="card">
    <img :src="product.image" alt="" width="80%" />
    <div class="container">
      <h4 :class="isMenProduct ? 'title-produk1' : 'title-produk'">
        <b> {{ product.title }} </b>
      </h4>
      <p class="category-produk">{{ product.category }}</p>
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