<template>
  <PlanetInfo
    :name="mars.name"
    :planetImg="planetImg"
    :overview="mars.overview.content"
    :overviewSource="mars.overview.source"
    :structure="mars.structure.content"
    :structureSource="mars.structure.source"
    :geology="mars.geology.content"
    :geologySource="mars.geology.source"
    :rotation="mars.rotation"
    :revolution="mars.revolution"
    :radius="mars.radius"
    :temperature="mars.temperature"
    assignedColor="D14C32"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      mars: data[3],
      planetImg: "planet-mars",
    };
  },
};
</script>

<style></style>
