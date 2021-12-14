<template>
  <PlanetInfo
    :name="saturn.name.toUpperCase()"
    :planetImg="planetImg"
    :overview="saturn.overview.content"
    :overviewSource="saturn.overview.source"
    :structure="saturn.structure.content"
    :structureSource="saturn.structure.source"
    :geology="saturn.geology.content"
    :geologySource="saturn.geology.source"
    :rotation="saturn.rotation"
    :revolution="saturn.revolution"
    :radius="saturn.radius"
    :temperature="saturn.temperature"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      saturn: data[5],
      planetImg: "planet-saturn",
    };
  },
};
</script>

<style></style>
