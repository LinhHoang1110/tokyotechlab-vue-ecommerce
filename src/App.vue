<template>
  <div data-app>
    <v-card class="overflow-hidden">
      <v-app-bar
        absolute
        color="white"
        elevate-on-scroll
        scroll-target="#scrolling-techniques-7"
      >
        <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->

        <v-toolbar-title style="font-size: 2rem"
          >Shop<span style="color: red">Clother</span></v-toolbar-title
        >
        <v-spacer></v-spacer>
        <v-autocomplete
          v-model="search"
          :search-input.sync="searchProduct"
          cache-items
          class="mx-4"
          flat
          hide-no-data
          hide-details
          label="Search products"
          solo-inverted
        ></v-autocomplete>
        <v-spacer></v-spacer>

        <v-btn class="ma-2 my-10" outlined color="indigo"> sign in </v-btn>
        <v-btn class="ma-2" outlined color="indigo"> sign up </v-btn>
        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet
        id="scrolling-techniques-7"
        class="overflow-y-auto"
        max-height="65"
      >
        <v-container style="height: 1500px"> </v-container>
      </v-sheet>
    </v-card>
    <div id="filter">
      <v-row>
        <v-col id="cateFilter" cols="12" sm="4">
          <v-select
            v-model="categoriesSelected"
            :items="categories"
            attach
            chips
            label="Chips"
            multiple
            @change="filterProductsByCate"
          ></v-select>
        </v-col>
        <v-col class="d-flex" cols="12" sm="4">
          <v-select v-model="priceProduct" @change="filterPrice" :items="prices" label="Standard"></v-select>
        </v-col>
      </v-row>
    </div>

    <!-- card -->
    <div v-if="productsFilter.length === 0" id="products">
      <v-card
        v-for="product in products"
        :key="product.id"
        class="mx-auto my-12 d-flex cards"
        max-width="300px"
      >
        <template slot="progress">
          <v-progress-linear
            color="deep-purple"
            height="10"
            indeterminate
          ></v-progress-linear>
        </template>

        <v-img class="img" height="200" :src="product.image"></v-img>

        <v-card-title>{{ product.title }}</v-card-title>

        <v-card-text>
          <v-row align="center" class="mx-0"> </v-row>

          <div style="margin-top: 10px; color: red" class="my-4 subtitle-1">
            $ {{ product.price }}
          </div>

          <div>
            {{ product.description }}
          </div>
        </v-card-text>

        <v-divider class="mx-4"></v-divider>
      </v-card>
    </div>

    <div v-else id="products">
      <v-card
        v-for="product in productsFilter"
        :key="product.id"
        class="mx-auto my-12 d-flex cards"
        max-width="300px"
      >
        <template slot="progress">
          <v-progress-linear
            color="deep-purple"
            height="10"
            indeterminate
          ></v-progress-linear>
        </template>

        <v-img class="img" height="200" :src="product.image"></v-img>

        <v-card-title>{{ product.title }}</v-card-title>

        <v-card-text>
          <v-row align="center" class="mx-0"> </v-row>

          <div style="margin-top: 10px; color: red" class="my-4 subtitle-1">
            $ {{ product.price }}
          </div>

          <div>
            {{ product.description }}
          </div>
        </v-card-text>

        <v-divider class="mx-4"></v-divider>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      products: [],
      categories: [],
      categoriesSelected: [],
      prices: [],
      search: "",
      productsFilter: [],
      priceProduct: 0
    };
  },
  computed: {},
  created() {
    this.fetchCategoriesData();
    this.fetchProductsData();
  },
  methods: {
    filterPrice(){
      const result = this.products.filter(product => product.price === this.priceProduct)
      this.productsFilter = result;
    },
    filterProductsByCate() {
      const result = this.products.filter((product) => {
        const check = this.categoriesSelected.includes(product.category);
        return check;
      });
      this.productsFilter = result;
    },
    fetchProductsData() {
      axios
        .get("https://fakestoreapi.com/products")
        .then((products) => {
          this.products = products.data;
          this.prices = products.data.map((product) => product.price);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    fetchCategoriesData() {
      axios
        .get("https://fakestoreapi.com/products/categories")
        .then((categories) => {
          this.categories = categories.data;
          this.categoriesSelected = categories.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
#products {
  width: 100%;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.cards {
  margin-top: 50px;
}
.v-divider {
  border: none;
}
#filter {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 50px;
}
.row {
  display: flex;
  justify-content: center;
}
</style>