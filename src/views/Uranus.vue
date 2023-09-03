<template>
  <PlanetInfo
    :name="uranus.name"
    :planetImg="planetImg"
    :overview="uranus.overview.content"
    :overviewSource="uranus.overview.source"
    :structure="uranus.structure.content"
    :structureSource="uranus.structure.source"
    :geology="uranus.geology.content"
    :geologySource="uranus.geology.source"
    :rotation="uranus.rotation"
    :revolution="uranus.revolution"
    :radius="uranus.radius"
    :temperature="uranus.temperature"
    assignedColor="1EC1A2"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      uranus: data[6],
      planetImg: "planet-uranus",
    };
  },
};
</script>

<style></style>
