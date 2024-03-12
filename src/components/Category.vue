<template>
  <div class="category-list">
    <div class="category" v-for="(category, index) in categories" :key="index">
      <div
          class="category-card"
          @click="selectCategory(category)"
          :class="{ 'active': selectedCategory === category }"
      >
        <div class="card-content">
          <img :src="category.img" alt="Category Image" />
          <div class="category-title">
            {{ category.title }}
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    categories: [
      { img: "public/egg.png", title: "Eggs" },
      { img: "public/cheese.png", title: "Cheese" },
      { img: "public/cookie.png", title: "Bakery and Sweets" },
      { img: "public/soap.png", title: "Soaps and Lotions" },
      { img: "public/shirt.png", title: "T-shirts" },
      { img: "public/cup.png", title: "Mugs" },
      { img: "public/goat1.png", title: "Accessories" },
    ]
  })

}

</script>

<style scoped>
.category-list {
  display: flex;
  justify-content: center;
  align-items: center;
}

.category {
  margin: 0 10px;
}

.category-card {
  cursor: pointer;
  display: flex;
  background-color: white;
  border: 1px solid #d5f0db;
  border-radius: 8px;
  padding: 10px;
  transition: background-color 0.3s;
  height: 150px;
  width: 150px;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.category-card:hover {
  background-color: #e09062;
}

.category-card.active {
  background-color: #d5f0db;
}

.card-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.category-card img {
  max-height: 80px;
  max-width: 80px;
  object-fit: contain;
}

.category-title {
  font-weight: bold;
  margin-top: 10px;
  text-align: center;
  height: 20px;
  font-size: 14px;
}
</style>
