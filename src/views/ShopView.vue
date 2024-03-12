<template>
  <div class="shop">
    <div class="shop-image">
      <img src="public/eggsinbasket.jpeg" alt="Eggs in a Basket" />
      <div class="image-overlay">
        <h2 class="title1">Order your food</h2>
        <h2 class="title2">From TalTech store</h2>
        <h3 class="green-text">#Free Delivery</h3>
      </div>
    </div>
    <div class="custom-toolbar">
      <div class="toolbar-title">
        Category
      </div>
    </div>
    <br>
    <Category />
    <br>
    <div style="height: 10px; background-color: #e09062;"></div>
    <br>
    <div class="products">
      <div class="product" v-for="(product, i) in categories[0].products" :key="i">
        <Product v-bind:product="product"/>
      </div>
    </div>
    <br>
    <br>
    <div style="height: 10px; background-color: #e09062;"></div>
    <div class="pack-title">
      Popular bundle packs
    </div>
    <div class="packs">
      <div class="pack" v-for="(pack, i) in categories[0].packs" :key="i">
        <Pack v-bind:pack="pack"/>
      </div>
    </div>
    <div style="height: 50px; background-color: #e09062;"></div>
  </div>

</template>

<script>
import Category from "@/components/Category.vue";
import Product from "@/components/Product.vue";
import Pack from "@/components/Pack.vue";
import axios from 'axios';

export default {
  name: "ShopView",
  components: {Pack, Product, Category},
  async mounted() {
    try {
      const response = await axios.get('https://goats.webhop.me/api/items');
      this.categories[0].products = response.data; // Update your products data with the fetched data
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  },
  data: () => ({
    bpm: 0,
    categories: [
      {
        title: "Eggs",
        products: [
          { img: "public/eggs.png", title: "6 Eggs", subtitle: "Chicken", price: "$3" },
          { img: "public/eggs.png", title: "9 Eggs", subtitle: "Chicken", price: "$5" },
          { img: "public/eggs.png", title: "6 Eggs", subtitle: "Chicken", price: "$3" },
          { img: "public/eggs.png", title: "9 Eggs", subtitle: "Chicken", price: "$5" },
          { img: "public/eggs.png", title: "6 Eggs", subtitle: "Chicken", price: "$3" },
          { img: "public/eggs.png", title: "9 Eggs", subtitle: "Chicken", price: "$5" },
        ],
        packs: [
          { img: "public/eggs.png", title: "6 Eggs", subtitle: "3 Chicken, 3 Goose", price: "$5" },
          { img: "public/eggs.png", title: "10 Eggs", subtitle: "5 Chicken, 5 Goose", price: "$9" },
          { img: "public/eggs.png", title: "14 Eggs", subtitle: "7 Chicken, 7 Goose", price: "$13" },
          { img: "public/eggs.png", title: "16 Eggs", subtitle: "8 Chicken, 8 Goose", price: "$15" },
        ],
      },
      {
        title: "Cheese",
        products: [
          { img: "cheese.png", title: "Cheddar Cheese", subtitle: "200g", price: "$5" },
          { img: "cheese.png", title: "Mozzarella Cheese", subtitle: "250g", price: "$6" },
          // Add more products for this category
        ],
        packs: [
          { img: "pack3.png", title: "Cheese Lovers Pack", subtitle: "Variety of Cheeses", price: "$15" },
          // Add more packs for this category
        ],
      }
    ],
    toggle_exclusive: 1,
  }),
  methods: {
    toggleExclusive(value) {
      this.toggleExclusive = value;
    },
  },
}
</script>

<style scoped>
.products {
  display: flex;
  flex-wrap: wrap;
  justify-content: left;
  gap: 20px;

  margin-left: calc((100% - (4 * (250px + 20px))) / 2);
  margin-right: calc((100% - (4 * (250px + 20px))) / 2);
}

.packs {
  display: flex;
  flex-wrap: wrap;
  justify-content: left;
  gap: 20px;
  background-color: #e09062;
  padding-left: calc((100% - (4 * (270px + 20px))) / 2);
  padding-right: calc((100% - (4 * (270px + 20px))) / 2);
}

.pack-title {
  font-size: 24px;
  font-weight: bold;
  color: #181818;
  justify-content: flex-start;
  background-color: #e09062;
}

.shop {
  text-align: center;
}

.shop-image {
  position: relative;
  max-width: 100%;
  height: 30vh;
  overflow: hidden;
  display: flex;
  align-items: flex-end;
}

.shop-image img {
  width: 100%;
  height: 40%;
  object-fit: cover;
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("../../public/eggsinbasket.jpeg");
  background-size: cover;
  color: #fff;
  text-align: left; /* Align text to the left */
  padding: 20px; /* Add padding to push text away from the corner */
  box-sizing: border-box;
}

.title1 {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 5px;
  margin-left: calc((100% - (4 * 290px)) / 2);
}

.title2 {
  font-size: 24px;
  font-weight: bold;
  margin-left: calc((100% - (4 * 290px)) / 2);
}

.green-text {
  color: #ff001a;
  font-size: 24px;
  margin-top: 10px; /* Adjust as needed */
  margin-left: calc((100% - (4 * 290px)) / 2);
}

.custom-toolbar {
  display: flex;
  align-items: center;
  background: transparent;
  padding: 8px 16px;
}

.toolbar-title {
  font-size: 30px;
  font-weight: bold;
  margin-left: calc((100% - (4 * 290px)) / 2);
}


</style>
