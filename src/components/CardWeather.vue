<template>
  <div v-for="(data, index) in cuaca" :key="index">
    <div class="card d-flex justify-content-center align-items-center flex-column">
      <div class="item fs-2 fw-light">{{ data.kota }}</div>
      <div class="item image"><img :src="'../img/' + data.status + '.png'" :alt="data.status"></div>
      <div class="item fs-1 fw-bold">{{ data.suhu }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardWeather',
  props: {
    cuaca: Array
  },
  methods: {
  getWeatherImage(cuaca) {
    // Mengembalikan path gambar sesuai dengan cuaca
    return `<img src="../assets/${cuaca}.png">`;
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  width: 300px;
  border-radius: 20px;
  height: 400px;
}
.item {
  width: 100%;
  height: 30%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.item img {
  width: 40%;
}
.image {
  height: 40%;
}
</style>
