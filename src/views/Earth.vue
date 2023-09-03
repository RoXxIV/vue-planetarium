<template>
  <PlanetInfo
    :name="earth.name"
    :planetImg="planetImg"
    :overview="earth.overview.content"
    :overviewSource="earth.overview.source"
    :structure="earth.structure.content"
    :structureSource="earth.structure.source"
    :geology="earth.geology.content"
    :geologySource="earth.geology.source"
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
      earth: data[2],
      planetImg: "planet-earth",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.earth.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.earth.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.earth.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.earth.temperature,
      ease: "power4.out",
    });
  },
};
</script>
