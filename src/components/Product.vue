<template>
      <div class="product-card">
        <div class="product-image">
          <img class="product-img" :src="product.img" alt="Product Image" />
        </div>
        <div class="product-details">
          <h3 class="product-title">{{ product.name }}</h3>
          <p class="product-subtitle">{{ product.description }}</p>
          <p class="product-price">{{ product.price }}</p>
        </div>
        <div class="product-actions">
          <button @click="decrement" class="product-action">-</button>
          <span class="product-quantity">{{ bpm }}</span>
          <button @click="increment" class="product-action">+</button>
          <button class="product-action buy-button">
            <i class="mdi-shopping"></i>
          </button>
        </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      bpm: 0
    }),
    methods: {
      decrement () {
        this.bpm--
      },
      increment () {
        this.bpm++
      },

    },
    props: ["product"],
    setup(props) {
      // we have props here
      console.log(props.product)
    }
  }

</script>

<style scoped>
.product-card {
  border: 1px solid #ccc;
  border-radius: 8px;
  overflow: hidden;
  text-align: center;
  width: 250px; /* Set a fixed width for the product card */
  height: 250px; /* Set a fixed height for the product card */
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 16px;
}

.product-card:hover {
  background-color: #d9a286;
}

.product-image {
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-img {
  max-height: 100px;
  max-width: 150px;
  object-fit: contain;
}

.product-details {
  text-align: center;
}

.product-title {
  font-size: 18px;
  font-weight: bold;
}

.product-subtitle {
  font-size: 14px;
  color: #888;
}

.product-price {
  font-size: 20px;
  font-weight: bold;
  color: #009900;
}

.product-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f0f0f0;
  border-radius: 8px;

  padding: 8px 16px;
}

.product-action {
  border: none;
  background-color: transparent;
  cursor: pointer;
  font-size: 15px;
}

.buy-button {
  background-color: #e09062;
  color: white;
  border-radius: 50%;
  padding: 12px;
  font-size: 24px;
  cursor: pointer;
}

</style>