<template>
      <div class="search-wrapper panel-heading col-sm-12">
    <input type="text" v-model="search" placeholder="Search" /> <br> <br>
      </div>
  <div class="wrapper">
    <select v-model="kitchenStuff">
      
      <option value="kitchenware">Kitchenware</option>
      <option v-for="category in categories" :key="category">{{ category }}</option>
    </select>

    <div v-if="category.length">
      <div class="prodCard" v-for="product in category" :key="product.id">
        <div class="card-header">
          <h2>{{ product.name }}</h2>
        </div>
        <div class="card-body">
          <img :src="product.image" :alt="product.name" loading="lazy">
          <p :class="product.price">R{{ product.price }}</p>
        </div>
        <div class="card-footer">
          <p>{{ product.category }}</p>
        </div>
      </div>
    </div>
    <div v-else>
      <p>Sorry, no products were found in this category.</p>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  components: {},
  data() {
    return {
      products: [
      {
        id: 1,
        name: "Bubble Candle",
        price: 60,
        category: "candle",
        description: "perfect gift for someone with minimalistic style.",
        image: "https://i.postimg.cc/kgFrpCrN/Screenshot-2023-12-05-085816.png"
    },
    {
        id: 2,
        name: "Bamboo Steamer",
        price: 250,
        category: "kitchenware",
        description: "Steam bao, fish or vegetables, essential for every Asian kitchen",
        image: "https://i.postimg.cc/9MGqyQg9/Screenshot-2023-12-05-085221.png"
    },
    {
        id: 3,
        name: "Polka Mustard Set",
        price: 400,
        category: "kitchenware",
        description: "12 piece set. includes 4 dinner plates, 4 side plates and 4 soup bowls",
        image: "https://i.postimg.cc/m2K2sB60/Screenshot-2023-12-05-084745.png"
    },
    {
        id: 4,
        name: "Starter Baking Set",
        price: 300,
        category: "kitchenware",
        description: "includes two silicone baking trays and a lava cake mold.",
        image: "https://i.postimg.cc/RZ367gjz/Screenshot-2023-12-05-085321.png"
    },
    {
        id: 5,
        name: "Glass Container",
        price: 150,
        category: "kitchenware",
        description: "could be used for make-up, hands-towels or lingerie.",
        image: "https://i.postimg.cc/jd1Y7cHN/Screenshot-2023-12-05-084903.png"
    },
    {
        id: 6,
        name: "Bear Candle",
        price: 80,
        category: "candle",
        description: "perfect gift for a baby shower or to display in a nursery room",
        image: "https://i.postimg.cc/Bnqvw3Qx/Screenshot-2023-12-05-085614.png"
    },
    {
        id: 7,
        name: "I Love You Candle",
        price: 75,
        category: "candle",
        description: "Love is in the air, quite literally... Amazing gift for date night or Valentines Day.",
        image: "https://i.postimg.cc/yxfS7tSk/Screenshot-2023-12-05-085650.png"
    },
  ],
  search: "",
  categories: ['other'],
    kitchenStuff: 'kitchenware'
    }
  }, computed: {
    category() {
      let filteredProducts = this.products;

      // Filter by category
      if (this.kitchenStuff !== 'other') {
        filteredProducts = filteredProducts.filter(product => product.category === this.kitchenStuff);
      }

      // Filter by search query
      if (this.search) {
        const searchTerm = this.search.toLowerCase();
        filteredProducts = filteredProducts.filter(product =>
          product.name.toLowerCase().includes(searchTerm) ||
          product.description.toLowerCase().includes(searchTerm)
        );
      }
      return filteredProducts;
    },
  },
};

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
