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
      mars: data[3],
      planetImg: "planet-mars",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.mars.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.mars.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.mars.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.mars.temperature,
      ease: "power4.out",
    });
  },
};
</script>
