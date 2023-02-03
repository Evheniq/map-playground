<template>
  <h2 style="margin-top: 50px">{{ mapInfo.name }} <button @click="addBorder">Show border</button></h2>
  <div class="map" :ref="mapInfo.name" :id="mapInfo.name">

  </div>
</template>

<script>
import data from "./UA_country.json";

export default {
  name: "mapCustom",
  props: {
    mapInfo: {
      required: true
    }
  },
  data() {
    return {
      map: undefined,
    }
  },
  methods: {
    addBorder(){
      L.geoJSON(data, {
        color: "#ff2424",
        weight: 3,
        opacity: .6,
        lineJoin: 'round',
        stroke: true,
        fill:false
      }).addTo(this.map);
    }
  },
  mounted() {
    this.map = L.map(this.$refs[this.mapInfo.name]).setView([48.505, 32.09], 6);

    L.tileLayer(this.mapInfo.link, {
      attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
    }).addTo(this.map);
  }
}
</script>

<style scoped>
.map {
  height: 500px;
}
</style>