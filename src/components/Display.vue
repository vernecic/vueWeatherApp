<template>
  <div class="text-center" v-if="vrijemeData">
    <div>
      <div
        v-if="vrijemeData && vrijemeData.weather[0].description === 'clear sky'"
        class="text-8xl"
      >
        ☀️
      </div>
      <div
        v-else-if="vrijemeData.weather[0].description === 'rain'"
        class="text-8xl"
      >
        🌧️
      </div>
      <div
        v-else-if="
          vrijemeData && vrijemeData.weather[0].description === 'broken clouds'
        "
        class="text-8xl"
      >
        🌥️
      </div>
      <div
        v-else-if="
          vrijemeData && vrijemeData.weather[0].description === 'few clouds'
        "
        class="text-8xl"
      >
        ☁️
      </div>
      <div
        v-else-if="
          vrijemeData &&
          vrijemeData.weather[0].description === 'scattered clouds'
        "
        class="text-8xl"
      >
        🌤️
      </div>
      <div
        v-else-if="
          vrijemeData &&
          vrijemeData.weather[0].description === 'overcast clouds'
        "
        class="text-8xl"
      >
        ☁️
      </div>
      <div
        v-else-if="
          vrijemeData && vrijemeData.weather[0].description === 'shower rain'
        "
        class="text-8xl"
      >
        🌧️
      </div>
      <div
        v-else-if="
          vrijemeData && vrijemeData.weather[0].description === 'thunderstorm'
        "
        class="text-8xl"
      >
        ⚡
      </div>
      <div
        v-else-if="vrijemeData && vrijemeData.weather[0].description === 'snow'"
        class="text-8xl"
      >
        ❄️
      </div>
      <div
        v-else-if="
          (vrijemeData && vrijemeData.weather[0].description === 'mist') ||
          vrijemeData.weather[0].description === 'fog' ||
          vrijemeData.weather[0].description === 'haze'
        "
        class="text-8xl"
      >
        🌫️
      </div>

      <div class="mt-5 text-2xl">
        {{ vrijemeData.name }}, {{ vrijemeData.sys.country }}
      </div>
    </div>
    <div class="text-2xl">{{ Math.round(vrijemeData.main.feels_like) }}°C</div>
    <div class="font-[400]">{{ vrijemeData.weather[0].description }}</div>
    <div class="grid grid-cols-2 gap-5 mt-5">
      <div class="flex flex-col border-[0.5px] rounded-lg p-2">
        <h3>Wind speed:</h3>
        {{ vrijemeData.wind.speed }}
      </div>
      <div class="flex flex-col border-[0.5px] rounded-lg p-2">
        <h3>Humidity:</h3>
        {{ vrijemeData.main.humidity }}%
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  vrijemeData: Object,
});
</script>
