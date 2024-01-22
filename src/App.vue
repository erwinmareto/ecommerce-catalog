<script setup>
import HomePage from './components/HomePage.vue';
import NotFound from './components/NotFound.vue';
</script>

<template>
  <div v-if="isLoading" class="container">
    <div class="loader" />
  </div>

  <div v-else-if="data === null" id="not-found-section">
    <NotFound :next="changePage" />
  </div>

  <div v-else-if="data?.category === 'men\'s clothing'" id="men-section">
    <HomePage :item="data" :next="changePage" type="men" />
  </div>

  <div v-else-if="data?.category === 'women\'s clothing'" id="women-section">
    <HomePage :item="data" :next="changePage" type="women" />
  </div>
  <!-- <NotFound /> -->
</template>

<script>
export default {
  data() {
    return {
      data: null,
      isLoading: false,
      current: 1
    }
  },
  mounted() {
    this.fetchData(this.current);
  },
  methods: {
    async fetchData(id) {
      this.isLoading = true;
      const response = await fetch(`https://fakestoreapi.com/products/${id}`);
      const data = await response.json();
      if (data.category !== "men's clothing" && data.category !== "women's clothing") {
        this.data = null
        this.isLoading = false;
        return
      }
      else if (id >= 20) {
        this.data = data
        this.isLoading = false;
        this.current = 0;
        return
      }
      this.data = data;
      this.isLoading = false;
    },
    async changePage() {
      this.current++
      await this.fetchData(this.current)
    }
  },
}
</script>


