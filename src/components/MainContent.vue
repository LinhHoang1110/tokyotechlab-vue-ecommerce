<template>
  <div id="mainContent">
    <el-row style="margin-bottom: 50px">
      <el-col :span="5">
        <el-select
          @change="filterPrice"
          v-model="priceSelected"
          placeholder="Prices"
        >
          <el-option
            v-for="(price, index) in prices"
            :key="index"
            :value="price"
          >
          </el-option>
        </el-select>
      </el-col>
      <el-col :span="5">
        <el-select
          v-model="catesSelected"
          multiple
          collapse-tags
          style="margin-left: 20px"
          placeholder="Categories"
          @change="filterCates"
        >
          <el-option v-for="cate in cates" :key="cate" :value="cate">
          </el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row>
      <el-col v-if="filterProducts.length === 0">
        <el-card
          v-for="product in products"
          :key="product.id"
          :body-style="{ padding: '0px' }"
        >
          <img :src="product.image" class="image" />
          <div style="padding: 14px">
            <p style="margin-bottom: 100px">{{ product.description }}</p>
            <b>$ {{ product.price }}</b>
            <div class="block">
              <el-rate v-model="value1"></el-rate>
            </div>
            <el-button type="primary" plain
              ><i style="margin-right: 5px" class="el-icon-star-off"></i
              >Watch</el-button
            >
          </div>
        </el-card>
      </el-col>
      <el-col v-else>
        <el-card
          v-for="product in filterProducts"
          :key="product.id"
          :body-style="{ padding: '0px' }"
        >
          <img :src="product.image" class="image" />
          <div style="padding: 14px">
            <p style="margin-bottom: 100px">{{ product.description }}</p>
            <b>$ {{ product.price }}</b>
            <div class="block">
              <el-rate v-model="value1"></el-rate>
            </div>
            <el-button type="primary" plain
              ><i style="margin-right: 5px" class="el-icon-star-off"></i
              >Watch</el-button
            >
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      value1: null,
      cates: [],
      products: [],
      prices: [],
      priceSelected: null,
      catesSelected: [],
      filterProducts: [],
    };
  },
  created() {
    this.fetchCates();
    this.fetchProducts();
  },
  methods: {
    filterPrice() {
      const result = this.products.filter(product => product.price === this.priceSelected)
      this.filterProducts = result;
    },
    filterCates() {
      const result = this.products.filter((product) => {
        const check = this.catesSelected.includes(product.category);
        return check;
      });
      this.filterProducts = result;
    },
    fetchCates() {
      axios.get("https://fakestoreapi.com/products/categories").then((res) => {
        this.cates = res.data;
        console.log(this.cates);
      });
    },
    fetchProducts() {
      axios.get("https://fakestoreapi.com/products").then((res) => {
        this.products = res.data;
        this.prices = this.products.map((product) => product.price);
      });
    },
  },
};
</script>

<style scoped>
.bottom {
  margin-top: 13px;
  line-height: 12px;
}

.image {
  margin-top: 30px;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
  display: block;
  max-height: 150px;
}

.el-card {
  position: relative;
  margin-bottom: 10px;
  width: 30%;
}
.el-col {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
#mainContent {
  border-left: 1px solid rgb(224, 224, 224);
}
b {
  font-size: 25px;
  position: absolute;
  top: 400px;
}
.block {
  position: absolute;
  bottom: 10px;
  /* padding-top: 50px */
}
.el-button {
  position: absolute;
  bottom: 10px;
  right: 20px;
}
</style>