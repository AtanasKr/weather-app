<template>
  <Header />
  <SearchInput />
  <MainCard />
</template>

<script>
import Header from './components/Header.vue';
import SearchInput from './components/SearchInput.vue'
import MainCard from './components/MainCard.vue'
export default {
  components: {
    Header,
    SearchInput,
    MainCard
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
}
</style>
