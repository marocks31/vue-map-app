<template>
  <div class="about">
    <div id="map"></div>
  </div>
</template>

<script>
/* global mapboxgl */
export default {
  data: function () {
    return {};
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MY_API_KEY;
    const map = new mapboxgl.Map({
      container: "map", // container ID
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-87.6298, 41.8781], // starting position [lng, lat]
      zoom: 9, // starting zoom
    });
    console.log(map);
  },
  methods: {},
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  height: 300px;
  width: 100%;
}
</style>
