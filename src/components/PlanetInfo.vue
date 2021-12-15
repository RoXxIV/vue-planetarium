<template>
  <div>
    <section class="planet-review">
      <div class="planet-img">
        <img
          :src="getImg(planetImg)"
          v-if="showOverview || showGeology"
          alt=""
        />
        <img :src="getInternalImg(planetImg)" v-if="showStructure" />
        <img
          class="geology-img"
          :src="getGeology(planetImg)"
          v-if="showGeology"
        />
      </div>
      <div class="planet-resume">
        <div class="main-info">
          <h2>
            {{ name.toUpperCase() }}
          </h2>
          <div class="resume">
            <p v-if="showOverview">{{ overview }}</p>
            <p v-if="showStructure">
              {{ structure }}
            </p>

            <p v-if="showGeology">
              {{ geology }}
            </p>
          </div>
          <span class="source">
            <p>
              Source :
              <a
                v-if="showOverview"
                :href="overviewSource"
                class="source-link"
                target="_blank"
                rel="noopener noreferrer"
                >Wikipedia</a
              >
              <a
                v-if="showStructure"
                :href="structureSource"
                class="source-link"
                target="_blank"
                rel="noopener noreferrer"
                >Wikipedia</a
              >
              <a
                v-if="showGeology"
                :href="geologySource"
                class="source-link"
                target="_blank"
                rel="noopener noreferrer"
                >Wikipedia</a
              ><img src="../assets/images/icon-source.svg" alt="" />
            </p>
          </span>
        </div>

        <ul class="interaction-list">
          <li
            class="init-button"
            :style="showOverview ? `background: #${assignedColor}` : null"
            @click="toggleOverview"
          >
            <span>01</span>OVERVIEW
          </li>
          <li
            class="init-button"
            :class="{ active: showStructure }"
            :style="showStructure ? `background: #${assignedColor}` : null"
            @click="toggleStructure"
          >
            <span>02</span>INTERNAL STRUCTURE
          </li>
          <li
            class="init-button"
            :class="{ active: showGeology }"
            :style="showGeology ? `background: #${assignedColor}` : null"
            @click="toggleGeology"
          >
            <span>03</span>SURFACE GEOLOGY
          </li>
        </ul>
      </div>
    </section>
    <section class="data-planet">
      <div>
        <h4>ROTATION TIME</h4>
        <span>{{ rotation }}</span>
      </div>
      <div>
        <h4>REVOLUTION TIME</h4>
        <span>{{ revolution }}</span>
      </div>
      <div>
        <h4>RADIUS</h4>
        <span>{{ radius }}</span>
      </div>
      <div>
        <h4>AVERAGE TEMP</h4>
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
    "overviewSource",
    "structure",
    "structureSource",
    "geology",
    "geologySource",
    "rotation",
    "revolution",
    "radius",
    "temperature",
    "assignedColor",
  ],

  data() {
    return {
      showOverview: true,
      showStructure: false,
      showGeology: false,
      mycolor: "red",
      earth: "dark-blue",
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
.planet-review {
  display: flex;
  justify-content: space-between;
  padding: 126px 165px;
  /*overflow: hidden;*/
}
.planet-img {
  margin: auto;
  position: relative;
}
.planet-img img {
  max-width: 450px;
}
.geology-img {
  width: 199px;
  position: absolute;
  z-index: 3;
  right: 15%;
  top: 50%;
}
.planet-resume {
  width: 350px;
}
.planet-resume h2 {
  font-family: "Antonio", sans-serif;
  color: var(--white);
  font-size: 80px;
  line-height: 25px;
  letter-spacing: 2.6px;
}
.resume p {
  color: var(--white);
  line-height: 25px;
  font-size: 14px;
  font-family: "Spartan", sans-serif;
  height: 150px;
}
.source p {
  font-family: "Spartan", sans-serif;
  font-size: 14px;
  line-height: 25px;
  color: #ffffff;
  img {
    margin-left: 8px;
  }
}
.source-link {
  font-weight: bold;
  text-decoration: underline;
}
.interaction-list li {
  padding: 12px 28px;
  font-family: "Spartan", sans-serif;
  font-size: 12px;
  line-height: 25px;
  letter-spacing: 2.57px;
  font-weight: bold;
  color: white;
  cursor: pointer;
}
.interaction-list li:hover {
  background: #5e5e5e;
}

.interaction-list li span {
  margin-right: 25px;
  font-family: "Spartan", sans-serif;
  font-size: 12px;
  line-height: 25px;
  letter-spacing: 2.57px;
  font-weight: bold;
  color: white;
}
.data-planet {
  display: flex;
  justify-content: space-around;
  padding: 0px 165px;
  margin-bottom: 50px;
}
.data-planet div {
  border: 1px solid var(--gray);
  width: 20%;
  padding: 21px 23px;
}
.data-planet h4 {
  color: var(--white);
  line-height: 25px;
  letter-spacing: 1px;
  font-size: 11px;
  font-family: "Spartan", sans-serif;
  font-weight: bold;
  margin: 0;
}
.data-planet span {
  font-family: "Antonio", sans-serif;
  color: var(--white);
  letter-spacing: -1.5px;
  font-size: 40px;
}
/***___Media Queries___***/
/***___Tablet, Moins de 992px___***/
@media (max-width: 991.98px) {
  .planet-review {
    flex-direction: column;
    align-items: center;
    padding: 0px;
    margin-top: 30px;
  }
  .planet-img {
    text-align: center;
    img {
      max-width: 80%;
    }
  }
  .geology-img {
    top: 30%;
    left: 50%;
    width: 150px;
  }
  .planet-resume {
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 100%;
  }
  .planet-resume h2 {
    font-size: 48px;
  }
  .resume p {
    line-height: 22px;
    font-size: 11px;
  }
  .main-info {
    width: 300px;
  }
  .interaction-list {
    width: 280px;
  }
  .interaction-list li {
    padding: 8px 20px;

    font-size: 9px;

    letter-spacing: 1.93px;
  }
  .data-planet {
    padding: 0px 40px;
    margin-top: 10px;
  }
  .data-planet div {
    padding: 16px 16px;
  }
  .data-planet h4 {
    line-height: 16px;
    letter-spacing: 0.73px;
    font-size: 8px;
  }
  .data-planet span {
    letter-spacing: -0.9px;
    font-size: 24px;
  }
}
/***___Mobile, Moins de 668px___***/
@media (max-width: 667.98px) {
  .planet-img img {
    max-width: 50%;
  }
  .geology-img {
    width: 80px;
  }
  .planet-resume {
    flex-direction: column-reverse;
    margin-top: 20px;
  }
  .planet-resume h2 {
    font-size: 40px;
    text-align: center;
    margin-top: 12px;
  }
  .resume {
    text-align: center;
  }
  .interaction-list li {
    padding: 5px 0px;
    text-align: center;
  }
  .interaction-list li span {
    display: none;
  }
  .data-planet {
    display: flex;
    flex-direction: column;
    padding: 0px 24px;
  }
  .data-planet div {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 9px 24px;
    margin: 4px 0px;
  }
  .data-planet h4 {
    line-height: 16px;
    letter-spacing: 0.73px;
    font-size: 8px;
  }
  .data-planet span {
    letter-spacing: -0.75px;
    font-size: 20px;
  }
}
</style>
