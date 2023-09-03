<template>
  <PlanetInfo
    :name="mercury.name"
    :planetImg="planetImg"
    :overview="mercury.overview.content"
    :overviewSource="mercury.overview.source"
    :structure="mercury.structure.content"
    :structureSource="mercury.structure.source"
    :geology="mercury.geology.content"
    :geologySource="mercury.geology.source"
    :rotation="mercury.rotation"
    :revolution="mercury.revolution"
    :radius="mercury.radius"
    :temperature="mercury.temperature"
    assignedColor="419EBB"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      mercury: data[0],
      planetImg: "planet-mercury",
    };
  },
};
</script>

<style></style>
