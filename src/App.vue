<template>
  <Header />
  <SearchInput @weatherFetched="setWeatherData" />
  <MainCard :weatherData="weatherData" />
  <History :searchHistory="searchHistory" @remove-item="handleRemoveItem" />
</template>

<script>
import Header from './components/Header.vue';
import SearchInput from './components/SearchInput.vue'
import MainCard from './components/MainCard.vue'
import History from './components/History.vue';

export default {
  components: {
    Header,
    SearchInput,
    MainCard,
    History
  },
  data() {
    return {
      weatherData: null,
      searchHistory: []
    }
  },
  methods: {
    setWeatherData(data) {
      this.weatherData = data;
      this.searchHistory.push(data);
    },
    handleRemoveItem(index) {
      this.searchHistory.splice(index, 1);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

body {
  font-family: Inter;
  background-image: url('@/assets/main-bg.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 100vh;
  margin: 0;
}
</style>
