<script>
/* global mapboxgl */

export default {
  mounted: function () {
    this.mapFun();
  },
  methods: {
    mapFun: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MY_API_KEY;
      const map = new mapboxgl.Map({
        container: "map", // container ID
        style: "mapbox://styles/mapbox/streets-v11", // style URL
        center: [-84.388, 33.749], // starting position [lng, lat]
        zoom: 9, // starting zoom
        projection: "globe", // display the map as a 3D globe
      });

      map.on("style.load", () => {
        map.setFog({}); // Set the default atmosphere style
      });

      // create the popup
      const popup = new mapboxgl.Popup({ offset: 25 }).setText("Come enjoy the World of Coca-Cola.");
      // Create a default Marker and add it to the map.
      const marker1 = new mapboxgl.Marker().setLngLat([-84.3924, 33.7626]).setPopup(popup).addTo(map);
      console.log(marker1);
    },
  },
};
</script>

<template>
  <div id="map" style="height: 300px"></div>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>
<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}
</style>
