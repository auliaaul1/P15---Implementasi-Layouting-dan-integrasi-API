<script setup>
import { ref, onMounted } from "vue";
import api from "../services/api";

const products = ref([]);
const loading = ref(true);

const getProducts = async () => {
  try {
    const response = await api.get("/users?page=1");
    products.value = response.data.data;
  } catch (error) {
    console.error(error);
  } finally {
    loading.value = false;
  }
};

onMounted(() => {
  getProducts();
});
</script>

<template>
  <div class="home">
    <!-- HERO SECTION -->
    <section class="hero">
      <div class="hero-content">
        <h1>Healthy Skin, Happy Life</h1>
        <p>
          Discover premium skincare products that help your skin stay healthy,
          hydrated, and glowing every day.
        </p>

        <button>Shop Now</button>
      </div>
    </section>

    <!-- TITLE -->
    <div class="section-title">
      <h2>Featured Skincare Products</h2>
      <p>Our best collection for your beauty routine</p>
    </div>

    <!-- LOADING -->
    <div v-if="loading" class="loading">Loading products...</div>

    <!-- PRODUCT GRID -->
    <div v-else class="product-grid">
      <div v-for="item in products" :key="item.id" class="card">
        <img :src="item.avatar" :alt="item.first_name" />

        <div class="card-body">
          <h3>{{ item.first_name }} Serum</h3>

          <p class="desc">Brightening & Hydrating Skincare</p>

          <p class="price">
            Rp {{ (item.id * 50000).toLocaleString("id-ID") }}
          </p>

          <button class="btn-detail">View Product</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.home {
  width: 100%;
}

/* HERO */
.hero {
  height: 400px;
  border-radius: 25px;
  background: linear-gradient(135deg, #ffd6e7, #fff5f9);

  display: flex;
  justify-content: center;
  align-items: center;

  text-align: center;
  padding: 30px;
  margin-bottom: 50px;
}

.hero-content {
  max-width: 700px;
}

.hero h1 {
  font-size: 52px;
  color: #333;
  margin-bottom: 20px;
}

.hero p {
  color: #666;
  line-height: 1.7;
  font-size: 18px;
}

.hero button {
  margin-top: 25px;
  padding: 14px 35px;
  border: none;
  border-radius: 30px;
  background: #ec4899;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
}

.hero button:hover {
  transform: scale(1.05);
}

/* SECTION */
.section-title {
  text-align: center;
  margin-bottom: 30px;
}

.section-title h2 {
  color: #333;
  margin-bottom: 10px;
}

.section-title p {
  color: #777;
}

/* GRID */
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 25px;
}

/* CARD */
.card {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  transition: 0.3s;
}

.card:hover {
  transform: translateY(-8px);
}

.card img {
  width: 100%;
  height: 250px;
  object-fit: cover;
}

.card-body {
  padding: 20px;
}

.card-body h3 {
  color: #333;
  margin-bottom: 10px;
}

.desc {
  color: #777;
  font-size: 14px;
  margin-bottom: 15px;
}

.price {
  color: #ec4899;
  font-weight: bold;
  font-size: 18px;
  margin-bottom: 15px;
}

.btn-detail {
  width: 100%;
  border: none;
  background: #ec4899;
  color: white;
  padding: 12px;
  border-radius: 10px;
  cursor: pointer;
}

.btn-detail:hover {
  opacity: 0.9;
}

/* LOADING */
.loading {
  text-align: center;
  padding: 50px;
  font-size: 18px;
  color: #666;
}

/* RESPONSIVE */
@media (max-width: 768px) {
  .hero {
    height: auto;
    padding: 50px 20px;
  }

  .hero h1 {
    font-size: 34px;
  }

  .hero p {
    font-size: 16px;
  }
}
</style>
