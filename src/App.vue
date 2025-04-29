<template>
  <div class="flex flex-col justify-center">
    <Header></Header>
    <div class="flex justify-center items-center flex-col">
      <Search @emitCity="getWeather" />
      <Display
        :vrijemeData="vrijemeData"
        :forecastData="forecastData"
        class="mt-10 font-bold"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

import Header from "./components/Header.vue";
import Search from "./components/SearchBar.vue";
import Display from "./components/Display.vue";

const apiKey = import.meta.env.VITE_API_KEY;

const vrijemeData = ref(null);
const forecastData = ref(null);

const getWeather = async (city) => {
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

  const res = await fetch(url);
  console.log("Res: ", res);
  if (!res.ok) {
    console.error("There is an error", res.statusText);
    return;
  }
  const data = await res.json();
  vrijemeData.value = data;

  console.log(data);

  /*   const urlForecast = `https://pro.openweathermap.org/data/2.5/forecast/hourly?q=${city}&appid=${apiKey}&units=metric`;

  const resForecast = await fetch(urlForecast);
  console.log("ResForecast: ", resForecast);
  if (!resForecast.ok) {
    console.error("There is an error", resForecast.statusText);
    return;
  }
  const dataForecast = await resForecast.json();
  forecastData.value = dataForecast;

  console.log(forecastData); */
};
</script>
