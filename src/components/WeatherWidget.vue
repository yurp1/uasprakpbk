<!-- src/components/WeatherWidget.vue -->
<template>
  <q-page class="weather-widget">
    <q-card>
      <q-card-section>
        <div class="text-h6">Cuaca</div>
      </q-card-section>

      <q-card-section>
        <q-input
          filled
          v-model="location"
          label="Masukkan Lokasi"
          outlined
        />
        <q-btn
          class="full-width q-mt-md"
          color="primary"
          label="Cari"
          @click="fetchWeatherData"
        />
      </q-card-section>

      <q-card-section v-if="weatherData" class="q-pt-none">
        <q-list>
          <q-item>
            <q-item-section>
              <q-item-label caption>Lokasi</q-item-label>
              <q-item-label>{{ weatherData.name }}</q-item-label>
            </q-item-section>
          </q-item>
          <q-item v-if="weatherData.main">
            <q-item-section>
              <q-item-label caption>Temperatur</q-item-label>
              <q-item-label>{{ Math.round(weatherData.main.temp - 273.15) }}°C</q-item-label>
            </q-item-section>
          </q-item>
          <q-item v-if="weatherData.weather">
            <q-item-section>
              <q-item-label caption>Deskripsi</q-item-label>
              <q-item-label>{{ weatherData.weather[0].description }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>

      <q-card-section v-else class="text-grey">
        Loading data...
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      location: "",
      weatherData: null,
    };
  },
  methods: {
    async fetchWeatherData() {
      try {
        const apiKey = "b7bfca7b27a3485144fea086c50d09dc";
        const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=${apiKey}`;

        const response = await fetch(apiUrl);
        const data = await response.json();

        this.weatherData = data;
      } catch (error) {
        console.error("Error fetching weather data:", error);
      }
    },
  },
};
</script>

<style scoped>
.weather-widget {
  max-width: 400px;
  margin: 0 auto;
  margin-top: 50px;
}
</style>
