<script>
import BaseInput from "./components/BaseInput.vue";
import BaseButton from "./components/BaseButton.vue";
import Product from "./components/Product.vue";
export default {
  components: {
    BaseInput,
    BaseButton,
    Product,
  },
  data() {
    return {
      data: [
        {
          name: "Americano",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Espresso",
          image: "https://picsum.photos/48",
          status: "yellow",
          date: null,
        },
        {
          name: "Mocha",
          image: "",
          status: "green",
          date: null,
        },
        {
          name: "White Mocha",
          image: "",
          status: "yellow",
          date: 704305433,
        },
        {
          name: "Latte",
          image: "https://picsum.photos/48",
          status: "green",
          date: 1666715033,
        },
        {
          name: "Cappucino",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Walking with Giants",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Turbinator 2",
          image: "https://picsum.photos/48",
          status: "red",
          date: null,
        },
        {
          name: "Super Cali Fragilistic Expialidocious",
          image: "",
          status: "red",
          date: 704305433,
        },
        {
          name: "Baseball Hat",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Americano",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Espresso",
          image: "https://picsum.photos/48",
          status: "yellow",
          date: null,
        },
        {
          name: "Mocha",
          image: "",
          status: "green",
          date: null,
        },
        {
          name: "White Mocha",
          image: "",
          status: "yellow",
          date: 704305433,
        },
        {
          name: "Latte",
          image: "https://picsum.photos/48",
          status: "green",
          date: 1666715033,
        },
        {
          name: "Cappucino",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Walking with Giants",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
        {
          name: "Turbinator 2",
          image: "https://picsum.photos/48",
          status: "red",
          date: null,
        },
        {
          name: "Super Cali Fragilistic Expialidocious",
          image: "",
          status: "red",
          date: 704305433,
        },
        {
          name: "Baseball Hat",
          image: "https://picsum.photos/48",
          status: "green",
          date: null,
        },
      ],
    };
  },
};
</script>

<template>
  <div class="wrapper">
    <p class="title">Products</p>
    <div class="content">
      <div class="find">
        <base-input
          placeholder="Find a Product"
          style="width: 100%; margin-right: 8px"
        />
        <base-button>Search</base-button>
      </div>
      <div class="add">
        <base-input
          placeholder="Product Name"
          style="width: 100%; margin-right: 8px"
        />
        <base-button bg-color="#377364">Add Product</base-button>
      </div>
      <div class="products">
        <Product v-for="p in data" :key="p.name" :product="p" />
      </div>
    </div>
    <div class="footer">
      <p>
        page <span class="bold-text">1</span> of
        <span class="bold-text">2</span>
      </p>
      <p>
        Sort by <span class="bold-text">Sort</span>
        <select class="bold-text" name="sorting" id="product-sorting">
          <option value="order">Order</option>
          <option value="name">Name</option>
          <option value="status">Status</option>
        </select>
      </p>
      <select class="bold-text" name="pagination" id="product-pagination">
        <option value="5">5</option>
        <option value="5">10</option>
        <option value="5">15</option>
        <option value="5">20</option>
      </select>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  padding: 16px;
}
.title {
  font-family: "Bitter";
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 32px;
  color: #252526;
  margin-bottom: 16px;
}
.content {
  padding: 16px;
  background-color: #ffffff;
  border: 1px solid #e0e2e4;
  border-radius: 8px;
}
.find {
  display: flex;
  margin-bottom: 8px;
}
.add {
  display: flex;
  margin-bottom: 8px;
}
.footer {
  padding: 8px 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 12px;
}
.footer .bold-text {
  font-weight: 700;
}
select {
  background-color: transparent;
}
.products {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-column-gap: 16px;
}
@media screen and (max-width: 768px) {
  .products {
    display: grid;
    grid-template-columns: 1fr;
  }
}
</style>
