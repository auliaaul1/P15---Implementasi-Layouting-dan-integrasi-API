<template>
  <header class="header">
    <h2>D E R M A V I S E</h2>

    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/products">Products</router-link>
      <router-link to="/about">About</router-link>
      <router-link to="/contact">Contact</router-link>
    </nav>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 50px;
  background: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 1000;
  position: fixed;
  left: 0;
  width: 100%;
}

nav {
  display: flex;
  gap: 20px;
  align-items: center;
}

nav a {
  text-decoration: none;
  color: #333;
  font-weight: 600;
}

.router-link-active {
  color: #ec4899;
}
</style>
