<template>
  <div class="container-fluid d-flex justify-content-center align-items-center flex-column" style="height:100vh; overflow:hidden;">
    <div class="jam">{{ currentTime }}</div>
    <div class="row main">
      <div class="col-lg p-3 divide">
          <div class="fw-bold text-white text-start">Jakarta</div>
          <div class="d-flex position-relative status-cuaca">
            <img class="berawan" alt="berawan" src="/img/berawan.png">
            <div class="status text-white px-4 ps-5 fs-1">Berawan , 31° C</div>
          </div>
          <div class="line"></div>
          <div class="text-white text-start px-2 fs-1 fw-semibold">Keep Safe :)</div>
      </div>

      <div class="col-lg divides">
        <div class="d-flex justify-content-center align-items-center" style="width: 100%; height: 45px;">
          <div class="tgl text-white">{{ currentDate }} &nbsp; &nbsp; </div>
          <div class="line-tgl"></div>
        </div>
        <div class="d-flex justify-content-around card-container flex-row">
          <CardWeather :cuaca="cuaca"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CardWeather from './components/CardWeather.vue';

export default {
    name: "App",
    components: { CardWeather },
    data() {
      return {
        currentTime: '',
        currentDate: '',
        cuaca: [
          {
            kota: 'Yogyakarta',
            status: 'cerah',
            suhu: '32° C'
          },
          {
            kota: 'Bekasi',
            status: 'hujan',
            suhu: '32° C'
          },
        ]
      }
    },
    created() {
    this.updateTime(); // Panggil fungsi updateTime() saat komponen dibuat
    },
    mounted() {
      setInterval(this.updateTime, 1000); // Perbarui jam setiap 1 detik
    },
    methods: {
      updateTime() {
        const date = new Date();

        const day = date.toLocaleDateString("id-ID", { weekday: "long" });
        const month = date.toLocaleDateString("id-ID", { month: "long" });
        const dayOfMonth = date.getDate();
        const year = date.getFullYear();

        this.currentTime = date.toLocaleTimeString([], { hour12: false });
        this.currentDate = `${day}, ${dayOfMonth} ${month} ${year}`;
      }
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');
#app {
  font-family: 'Roboto', sans-serif;
  height: 100vh;
  background: linear-gradient(130.54deg, #27A5F9 26.95%, rgba(39, 165, 249, 0) 123.41%);
}
.main {
  width: 100%;
  padding: 0 60px;
}
.fw-bold {
  font-size: 110px;
}
.status-cuaca {
  margin-top: -25px;
}
.status {
  background: rgba(238, 238, 238, 0.5);
  border-radius: 10px;
  margin-left: 40px;
}
.line {
  background-color: white;
  width: 95%;
  height: 3px;
  margin-top: 40px;
}
.berawan {
  position: absolute;
  height: 60px;
}
.divide {
  display: flex;
  flex-direction: column;
  width: 50%;
}
.divides {
  display: flex;
  width: 50%;
  flex-direction: column;
}
.tgl {
  font-size: 27px;
  font-weight: 300;
}
.line-tgl {
  background-color: white;
  height: 3px;
  flex-grow: 1;
}
.card-container {
  margin-top: 10px;
}
.jam {
  position: absolute;
  top: 0;
  left: 5%;
  background-color: white;
  color: #27A5F9;
  padding: 5px 20px;
  font-size: 25px;
  border-radius: 0 0 10px 10px;
  font-weight: 700;
}
</style>
