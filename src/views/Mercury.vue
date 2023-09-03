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
      mercury: data[2],
      planetImg: "planet-mercury",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.mercury.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.mercury.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.mercury.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.mercury.temperature,
      ease: "power4.out",
    });
  },
};
</script>
