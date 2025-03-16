<template>
  <div id="app">
    <nav class="navbar">
      <h1>E-Commerce</h1>
    </nav>
    <div class="container">
      <h2>Bienvenue sur notre boutique en ligne</h2>
      <p>Services status:</p>
      <ul>
        <li>Products: {{ productStatus }}</li>
        <li>Users: {{ userStatus }}</li>
        <li>Cart: {{ cartStatus }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      productStatus: 'Checking...',
      userStatus: 'Checking...',
      cartStatus: 'Checking...'
    }
  },
  async mounted() {
    try {
      await axios.get('http://localhost:3000');
      this.productStatus = 'Online';
    } catch (error) {
      this.productStatus = 'Offline';
    }

    try {
      await axios.get('http://localhost:3001');
      this.userStatus = 'Online';
    } catch (error) {
      this.userStatus = 'Offline';
    }

    try {
      await axios.get('http://localhost:3002');
      this.cartStatus = 'Online';
    } catch (error) {
      this.cartStatus = 'Offline';
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
}

.navbar {
  background-color: #2c3e50;
  color: white;
  padding: 1rem;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0.5rem 0;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
