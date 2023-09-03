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
    :rotation="tweenedRotation"
    :revolution="tweenedRevolution"
    :radius="tweenedRadius"
    :temperature="tweenedTemperature"
    assignedColor="6D2ED5"
  ></PlanetInfo>
</template>

<script>
import gsap from "gsap";
import PlanetInfo from "../components/PlanetInfo.vue";
import data from "../data.json";

export default {
  components: { PlanetInfo },
  data() {
    return {
      neptune: data[2],
      planetImg: "planet-neptune",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.neptune.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.neptune.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.neptune.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.neptune.temperature,
      ease: "power4.out",
    });
  },
};
</script>
