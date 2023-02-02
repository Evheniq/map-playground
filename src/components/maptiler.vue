<template>
  <h2 style="margin-top: 50px">maptiler <button @click="addBorder">Show border</button></h2>

  <div id="maptiler"></div>
</template>

<script>
import data from "./UA_country.json";
export default {
  name: "maptiler",
  data() {
    return {
      key: "BvrtwMrSBaJInDrAfqu9",
      map: undefined,
    }
  },
  methods: {
    addBorder(){
      L.geoJSON(data, {
        color: "#eb0000",
        weight: 3,
        opacity: .3,
        lineJoin: 'round',
        stroke: true,
        fill:false
      }).addTo(this.map);
    }
  },
  mounted() {
    this.map = L.map('maptiler').setView([48.505, 32.09], 6);

    L.maplibreGL({
      attribution: "\u003ca href=\"https://www.maptiler.com/copyright/\" target=\"_blank\"\u003e\u0026copy; MapTiler\u003c/a\u003e \u003ca href=\"https://www.openstreetmap.org/copyright\" target=\"_blank\"\u003e\u0026copy; OpenStreetMap contributors\u003c/a\u003e",
      style: `https://api.maptiler.com/maps/a15b3407-30f5-4cf3-8fa2-d34509334a6f/style.json?key=BvrtwMrSBaJInDrAfqu9`
    }).addTo(this.map)
  }
}
</script>

<style scoped>
#maptiler{
  height: 500px;
}
</style>