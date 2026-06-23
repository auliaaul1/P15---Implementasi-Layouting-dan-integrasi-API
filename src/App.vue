<script setup>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
</script>

<template>
  <div class="container">
    <Header />

    <main class="content">
      <router-view />
    </main>

    <Footer />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body,
#app {
  min-height: 100vh;
}
html,
body {
  overflow-y: scroll;
}

body {
  margin: 0;
}

.container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.content {
  flex: 1;
  padding: 30px;
  background: #fff8fb;

  padding-top: 85px;
}
html {
  overflow-y: scroll;
}
</style>
