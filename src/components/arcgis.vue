<template>
  <h2 style="margin-top: 50px">{{ slug }} <button @click="addBorder">Show border</button></h2>

  <div :id="slug" style="height: 500px;"></div>
</template>

<script>
import data from "./UA_country.json";
export default {
  name: "arcgis",
  props: {
    slug: {
      type: String,
      required: true
    }
  },
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
    this.map = L.map(this.slug, {
      minZoom: 2
    }).setView([48.505, 32.09], 6);

    const apiKey = "AAPK60208ac8849d4f549ce2116640c129a0laz6rphhbdjPe4Y0N-jd8puPS0ONCcyAKp-_PfGHWTNfAMCpiSPSj0n1qrawjZMy";

    L.esri.Vector.vectorBasemapLayer(this.slug, {
      apiKey: apiKey
    }).addTo(this.map);

  }
}
</script>

<style scoped>

</style>