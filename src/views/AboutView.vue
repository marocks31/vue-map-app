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
    // create the popup
    const popup = new mapboxgl.Popup({ offset: 25 }).setText("Construction on the Washington Monument began in 1848.");

    // create DOM element for the marker
    const el = document.createElement("div");
    el.id = "marker";

    // create the marker
    new mapboxgl.Marker(el)
      .setLngLat([-87.6298, 41.8781])
      .setPopup(popup) // sets a popup on this marker
      .addTo(map);

    // Create a default Marker and add it to the map.
    const marker1 = new mapboxgl.Marker().setLngLat([-87.6298, 41.8781]).addTo(map);

    // Create a default Marker, colored black, rotated 45 degrees.
    const marker2 = new mapboxgl.Marker({ color: "black", rotation: 45 }).setLngLat([-87.6877, 42.0451]).addTo(map);
    console.log(map, marker1, marker2);
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
#marker {
  background-image: url("https://docs.mapbox.com/mapbox-gl-js/assets/washington-monument.jpg");
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

.mapboxgl-popup {
  max-width: 200px;
}
</style>
