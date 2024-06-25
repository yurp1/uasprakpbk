<!-- src/App.vue -->
<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title>
          Weather App
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <WeatherWidget />
    </q-page-container>
  </q-layout>
</template>

<script>
import WeatherWidget from './components/WeatherWidget.vue';

export default {
  name: 'App',
  components: {
    WeatherWidget
  }
};
</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0;
}
</style>
