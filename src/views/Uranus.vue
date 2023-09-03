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
      uranus: data[2],
      planetImg: "planet-uranus",
      tweenedRotation: 0,
      tweenedRevolution: 0,
      tweenedRadius: 0,
      tweenedTemperature: 0,
    };
  },
  mounted() {
    gsap.to(this, {
      duration: 1,
      tweenedRotation: this.uranus.rotation,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 1.5,
      tweenedRevolution: this.uranus.revolution,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2,
      tweenedRadius: this.uranus.radius,
      ease: "power4.out",
    });
    gsap.to(this, {
      duration: 2.5,
      tweenedTemperature: this.uranus.temperature,
      ease: "power4.out",
    });
  },
};
</script>
