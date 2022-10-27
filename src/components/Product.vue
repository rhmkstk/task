<script>
export default {
  name: "ProductComponent",
  props: {
    product: {
      type: Object,
      default: () => {},
    },
  },
};
</script>
<template>
  <div class="product">
    <div class="product-infos">
      <img class="product-image" :src="product.image" alt="product-image" />
      <div class="product-status-badge"></div>
      <p class="product-name product-text">{{ product.name }}</p>
    </div>
    <div>
      <span class="product-date product-text">{{ product.date }}</span>
      <select name="" id="">
        <option value="">a</option>
        <option value="">b</option>
        <option value="">c</option>
      </select>
    </div>
  </div>
</template>
<style scoped>
.product {
  padding: 12px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #f0f2f4;
}
.product-infos {
  display: flex;
  align-items: center;
}
.product-image {
  display: block;
  width: 24px;
  height: 24px;
  border-radius: 2px;
}
.product-status-badge {
  width: 9.33px;
  height: 9.33px;
  border-radius: 999px;
  background-color: red;
  margin: 0 11.33px;
}
.product-name {
  max-width: 24ch;
}
.product-text {
  font-weight: 400;
  font-size: 14px;
  line-height: 22px;
  color: #252526;
}
</style>
