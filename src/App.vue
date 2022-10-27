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
      products: [],
      itemsPerPage: 10,
      activePage: 1,
      sortQuery: "name",
      searchQuery: "",
    };
  },
  created() {
    this.setProductCountOnPage();
  },
  methods: {
    formatDate(pDate) {
      let date = new Date(pDate * 1000);
      const year = date.getFullYear();
      const mount = date.getMonth();
      const day = date.getDate();
      return `${mount}/${day}/${year}`;
    },
    sortProducts() {
      this.products = this.products.sort((a, b) =>
        a[this.sortQuery] < b[this.sortQuery]
          ? -1
          : a[this.sortQuery] > b[this.sortQuery]
          ? 1
          : 0
      );
    },
    setProductCountOnPage() {
      this.products = this.data.slice(0, this.itemsPerPage);
    },
    changeActivePage() {
      const end = this.itemsPerPage * this.activePage;
      const start = end - this.itemsPerPage;
      this.products = this.data.slice(start, end);
    },
  },
  computed: {
    totalPageCount() {
      return Math.ceil(this.data.length / this.itemsPerPage);
    },
    searchedProduct() {
      if (this.searchQuery) {
        return this.products.filter((item) => {
          return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every((n) => item.name.toLowerCase().includes(n));
        });
      } else {
        return this.products;
      }
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <p class="title">Products</p>
    <div class="content">
      <div class="find">
        <base-input
          v-model="searchQuery"
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
      <div class="product-list">
        <product
          v-for="(product, index) in searchedProduct"
          :key="index"
          :name="product.name"
          :image="product.image === '' ? undefined : product.image"
          :status="product.status"
          :date="
            product.date === null ? product.date : formatDate(product.date)
          "
        />
      </div>
    </div>
    <div class="footer">
      <p>
        page
        <select
          id="active-page"
          name="active-page"
          class="bold-text"
          @change="changeActivePage"
          v-model="activePage"
        >
          <option v-for="n in totalPageCount" :key="n" :value="n">
            {{ n }}
          </option>
          totalPageCount</select
        >of
        <span class="bold-text">{{ totalPageCount }}</span>
      </p>
      <p>
        Sort by <span class="bold-text">Sort</span>
        <select
          id="product-sorting"
          class="bold-text"
          name="sorting"
          v-model="sortQuery"
          @change="sortProducts"
        >
          <option value="name">Name</option>
          <option value="date">Date</option>
        </select>
      </p>
      <select
        v-model="itemsPerPage"
        id="product-pagination"
        name="pagination"
        class="bold-text"
        @change="setProductCountOnPage"
      >
        <option value="5">5</option>
        <option value="10">10</option>
        <option value="15">15</option>
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
.product-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-column-gap: 16px;
}
@media screen and (max-width: 768px) {
  .product-list {
    display: grid;
    grid-template-columns: 1fr;
  }
}
</style>
