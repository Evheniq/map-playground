<template>

  <drop-down
      title="Non License"
      link="https://www.trailnotes.org/FetchMap/TileServeSource.html"
  >
    <div v-for="map in mapsNonLicense" :key="map.name">
      <mapCustom :mapInfo="map" />
    </div>
  </drop-down>

  <drop-down
      title="License"
      link="https://docs.google.com/spreadsheets/d/1bUMOalRbZ9Zj5VGegHgj3ibIGTeMrLU_z7eLiXk7wYU/edit?usp=sharing"
  >
    <div v-for="map in mapsLicense" :key="map.name">
      <mapCustom :mapInfo="map" />
    </div>
    <maptiler/>
  </drop-down>

  <drop-down
      title="arcgis"
      link="https://developers.arcgis.com/documentation/mapping-apis-and-services/maps/services/basemap-layer-service/"
  >
    <arcgis slug="ArcGIS:Navigation"/>
    <arcgis slug="ArcGIS:DarkGray"/>
    <arcgis slug="ArcGIS:Streets"/>
    <arcgis slug="ArcGIS:StreetsRelief"/>
    <arcgis slug="ArcGIS:StreetsRelief:Base"/>
    <arcgis slug="ArcGIS:StreetsNight"/>
    <arcgis slug="ArcGIS:Topographic"/>
    <arcgis slug="ArcGIS:Topographic:Base"/>
    <arcgis slug="ArcGIS:Terrain"/>

    <arcgis slug="ArcGIS:Community"/>
    <arcgis slug="ArcGIS:Newspaper"/>
  </drop-down>

  <drop-down
      title="visicom"
      link="https://api.visicom.ua/uk/products/tiles/tiles-dataset"
  >
    <div v-for="map in mapsVisicom" :key="map.name">
      <visicom :mapInfo="map" />
    </div>
  </drop-down>


</template>

<script>
import mapCustom from "./components/mapCustom.vue";
import DropDown from "./components/dropDown.vue";
import Maptiler from "./components/maptiler.vue";
import Arcgis from "./components/arcgis.vue";
import Visicom from "./components/visicom.vue";

export default {
  components: {Visicom, Arcgis, Maptiler, DropDown, mapCustom},

  data() {
    return {
      mapsNonLicense: [
        {
          name: "cartodb",
          link: 'https://cartodb-basemaps-b.global.ssl.fastly.net/light_nolabels/{z}/{x}/{y}.png'
        },
        {
          name: "Esri:Topo",
          link: 'https://services.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer/tile/{z}/{y}/{x}.jpg'
        },
        {
          name: "ArcGIS Streets",
          link: 'http://services.arcgisonline.com/ArcGIS/rest/services/World_Street_Map/MapServer/tile/{z}/{y}/{x}'
        },
        {
          name: "NatGeo",
          link: 'http://services.arcgisonline.com/ArcGIS/rest/services/NatGeo_World_Map/MapServer/tile/{z}/{y}/{x}'
        },
        {
          name: "ESRI Satellite",
          link: 'http://a.tile.opentopomap.org/{z}/{x}/{y}.png'
        },
        {
          name: "USGS",
          link: 'https://basemap.nationalmap.gov/arcgis/rest/services/USGSTopo/MapServer/tile/{z}/{y}/{x}'
        }
      ],
      mapsLicense: [
        {
          name: "stamen",
          link: 'https://stamen-tiles.a.ssl.fastly.net/terrain/{z}/{x}/{y}.jpg'
        },
        {
          name: "thunderforestatlas",
          link: 'https://tile.thunderforest.com/atlas/{z}/{x}/{y}.png?apikey=95a888168fbd4b06b5596ffc9e30d527'
        },
        {
          name: "thunderforestneighbourhood",
          link: 'https://tile.thunderforest.com/neighbourhood/{z}/{x}/{y}.png?apikey=95a888168fbd4b06b5596ffc9e30d527'
        }
      ],
      mapsVisicom: [
        {
          name: "base",
          link: "https://tms2.visicom.ua/2.0.0/world,ua/base/{z}/{x}/{y}.png"
        },
        {
          name: "base_en",
          link: "https://tms2.visicom.ua/2.0.0/world,ua/base_en/{z}/{x}/{y}.png"
        },
      ]
    }
  }
}
</script>


<style scoped>


</style>
