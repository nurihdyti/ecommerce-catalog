<template>
  <div class="card">
    <div class="container center">
      <p>This product is unavailable to show</p>
      <button class="button-next2" @click="onButtonClick">Next product</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "NoProduct",
  methods: {
    onButtonClick() {
      this.$emit("onClickNext");
    },
  },
};
</script>