<template>
  <section>
    <div class="planet-img">
      <img :src="getImg(planetImg)" v-if="showOverview || showGeology" alt="" />
      <img :src="getInternalImg(planetImg)" v-if="showStructure" />
      <img :src="getGeology(planetImg)" v-if="showGeology" />
    </div>
    <div>
      <h2>{{ name }}</h2>
      <div>
        <p v-if="showOverview">{{ overview }}</p>
        <p v-if="showStructure">
          {{ structure }}
        </p>
        <p v-if="showGeology">
          {{ geology }}
        </p>
      </div>
      <span>
        <p>Source</p>
        <a :href="source">Wikipedia</a>
      </span>
      <ul>
        <li
          class="init-button"
          :class="{ active: showOverview }"
          @click="toggleOverview"
        >
          <span>01</span>OVERVIEW
        </li>
        <li
          class="init-button"
          :class="{ active: showStructure }"
          @click="toggleStructure"
        >
          <span>02</span>INTERNAL STRUCTURE
        </li>
        <li
          class="init-button"
          :class="{ active: showGeology }"
          @click="toggleGeology"
        >
          <span>03</span>SURFACE GEOLOGY
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "planet-info",
  props: ["name", "planetImg", "source", "overview", "structure", "geology"],
  data() {
    return {
      showOverview: true,
      showStructure: false,
      showGeology: false,
    };
  },
  methods: {
    getImg(img) {
      let image = require(`../assets/images/${img}.svg`);
      return image;
    },
    getInternalImg(img) {
      let image = require(`../assets/images/${img}-internal.svg`);
      return image;
    },
    getGeology(img) {
      let image = require(`../assets/images/${img}-geology.png`);
      return image;
    },
    toggleOverview() {
      this.showOverview = true;
      this.showStructure = false;
      this.showGeology = false;
    },
    toggleStructure() {
      this.showOverview = false;
      this.showStructure = true;
      this.showGeology = false;
    },
    toggleGeology() {
      this.showOverview = false;
      this.showStructure = false;
      this.showGeology = true;
    },
  },
};
</script>

<style scoped lang="scss"></style>
