<template>
    <br>

        <div class="pack-card">
          <div class="pack-image">
            <img class="pack-img" :src="pack.img" alt="Pack Image" />
          </div>
          <div class="pack-details">
            <h3 class="pack-title">{{ pack.title }}</h3>
            <p class="pack-subtitle">{{ pack.subtitle }}</p>
            <p class="pack-price">{{ pack.price }}</p>
          </div>
          <div class="pack-actions">
            <button @click="decrement" class="pack-action">-</button>
            <strong class="pack-quantity">{{ bpm }}</strong>
            <button @click="increment" class="pack-action">+</button>
            <button class="pack-action buy-button">
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
  props: ["pack"],
  setup(props) {
    // we have props here
    console.log(props.pack)
  }
}

</script>

<style scoped>

.pack-card {
  border: 1px solid #ccc;
  border-radius: 8px;
  overflow: hidden;
  text-align: center;
  width: 270px;
  height: 350px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 16px;
  background-color: white;
}

.pack-card:hover {
  background-color: #d9a286;
}

.pack-image {
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pack-img {
  max-height: 300px;
  max-width: 300px;
  object-fit: contain;
}

.pack-details {
  text-align: center;
}

.pack-title {
  font-size: 18px;
  font-weight: bold;
}

.pack-subtitle {
  font-size: 14px;
  color: #888;
}

.pack-price {
  font-size: 20px;
  font-weight: bold;
  color: #009900;
}

.pack-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f0f0f0;
  padding: 8px 16px;
  border-radius: 8px;
}

.pack-action {
  border: none;
  background-color: transparent;
  cursor: pointer;
  font-size: 24px;
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