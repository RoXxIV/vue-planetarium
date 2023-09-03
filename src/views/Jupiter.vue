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
      jupiter: data[2],
      planetImg: "planet-jupiter",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.jupiter.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.jupiter.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.jupiter.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.jupiter.temperature,
      ease: "power4.out",
    });
  },
};
</script>
