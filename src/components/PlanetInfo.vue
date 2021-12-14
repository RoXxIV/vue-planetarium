<template>
  <div>
    <section class="info-planet">
      <div class="planet-img">
        <img
          :src="getImg(planetImg)"
          v-if="showOverview || showGeology"
          alt=""
        />
        <img :src="getInternalImg(planetImg)" v-if="showStructure" />
        <img :src="getGeology(planetImg)" v-if="showGeology" />
      </div>
      <div class="planet-details">
        <h2>{{ name }}</h2>
        <div class="resume">
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
    <section class="data-planet">
      <div>
        <h3>ROTATION TIME</h3>
        <span>{{ rotation }}</span>
      </div>
      <div>
        <h3>REVOLUTION TIME</h3>
        <span>{{ revolution }}</span>
      </div>
      <div>
        <h3>RADIUS</h3>
        <span>{{ radius }}</span>
      </div>
      <div>
        <h3>AVERAGE TEMP</h3>
        <span>{{ temperature }}</span>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "planet-info",
  props: [
    "name",
    "planetImg",
    "source",
    "overview",
    "structure",
    "geology",
    "rotation",
    "revolution",
    "radius",
    "temperature",
  ],

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

<style scoped lang="scss">
.info-planet {
  display: flex;
  justify-content: space-between;
  padding: 126px 165px;
  .planet-img {
    margin: auto;
  }
  .planet-details {
    width: 350px;
    h2 {
      font-family: "Antonio", sans-serif;
      color: var(--white);
      font-size: 80px;
    }
    .resume p {
      color: var(--white);
      line-height: 25px;
      font-size: 14px;
      font-family: "Spartan", sans-serif;
    }
  }
}
</style>
