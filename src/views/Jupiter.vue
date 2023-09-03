<template>
  <PlanetInfo
    :name="jupiter.name"
    :planetImg="planetImg"
    :overview="jupiter.overview.content"
    :overviewSource="jupiter.overview.source"
    :structure="jupiter.structure.content"
    :structureSource="jupiter.structure.source"
    :geology="jupiter.geology.content"
    :geologySource="jupiter.geology.source"
    :rotation="jupiter.rotation"
    :revolution="jupiter.revolution"
    :radius="jupiter.radius"
    :temperature="jupiter.temperature"
    assignedColor="D83A34"
  ></PlanetInfo>
</template>

<script>
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";
export default {
  components: { PlanetInfo },
  data() {
    return {
      jupiter: data[4],
      planetImg: "planet-jupiter",
    };
  },
};
</script>

<style></style>
