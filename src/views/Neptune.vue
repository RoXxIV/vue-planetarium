<template>
  <PlanetInfo
    :name="neptune.name"
    :planetImg="planetImg"
    :overview="neptune.overview.content"
    :overviewSource="neptune.overview.source"
    :structure="neptune.structure.content"
    :structureSource="neptune.structure.source"
    :geology="neptune.geology.content"
    :geologySource="neptune.geology.source"
    :rotation="neptune.rotation"
    :revolution="neptune.revolution"
    :radius="neptune.radius"
    :temperature="neptune.temperature"
    assignedColor="2D68F0"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      neptune: data[7],
      planetImg: "planet-neptune",
    };
  },
};
</script>

<style></style>
