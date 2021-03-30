<template>
  <div id="map" style="width: 100vw; height: 100vh"></div>
</template>

<script>
import L from "leaflet";
import "leaflet/dist/leaflet.css";
export default {
  mounted() {
    var map = L.map("map").setView([51.505, -0.09], 13);

    L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
      attribution: "&copy map-test",
    }).addTo(map);
  },
};
</script>

<style>
</style>