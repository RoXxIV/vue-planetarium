<template>
  <PlanetInfo
    :name="saturn.name"
    :planetImg="planetImg"
    :overview="saturn.overview.content"
    :overviewSource="saturn.overview.source"
    :structure="saturn.structure.content"
    :structureSource="saturn.structure.source"
    :geology="saturn.geology.content"
    :geologySource="saturn.geology.source"
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
      saturn: data[5],
      planetImg: "planet-saturn",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.saturn.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.saturn.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.saturn.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.saturn.temperature,
      ease: "power4.out",
    });
  },
};
</script>
