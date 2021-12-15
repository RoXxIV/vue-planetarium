<template>
  <PlanetInfo
    :name="earth.name"
    :planetImg="planetImg"
    :overview="earth.overview.content"
    :overviewSource="earth.overview.source"
    :structure="earth.structure.content"
    :structureSource="earth.structure.source"
    :geology="earth.geology.content"
    :geologySource="earth.geology.source"
    :rotation="earth.rotation"
    :revolution="earth.revolution"
    :radius="earth.radius"
    :temperature="earth.temperature"
    assignedColor="6D2ED5"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      earth: data[2],
      planetImg: "planet-earth",
    };
  },
};
</script>

<style></style>
