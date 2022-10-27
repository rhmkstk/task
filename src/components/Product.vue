<script>
export default {
  name: "ProductComponent",
  props: {
    name: {
      type: String,
      default: "",
    },
    image: {
      type: String,
      default: "https://picsum.photos/48",
    },
    date: {
      type: [String, null],
      default: null,
    },
    status: {
      type: String,
      default: "green",
      validator: (val) => ["green", "red", "yellow"].includes(val),
    },
  },
  data() {
    return {
      statusses: {
        green: "#518103",
        red: "#C63434",
        yellow: "#E4D33A",
      },
    };
  },
};
</script>
<template>
  <div class="product">
    <div class="product-infos">
      <img class="product-image" :src="image" alt="product-image" />
      <div
        class="product-status-badge"
        :style="`background-color: ${this.statusses[status]}`"
      ></div>
      <p class="product-name product-text">{{ name }}</p>
    </div>
    <div class="product-infos">
      <div class="product-date product-text" v-if="date !== null">
        {{ date }}
      </div>
      <img src="../assets/icons/small-down.svg" alt="icon">
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
  margin: 0 11.33px;
}
.product-date {
  margin-right: 16px;
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
