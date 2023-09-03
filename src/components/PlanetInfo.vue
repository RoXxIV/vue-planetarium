<template>
  <div>
    <section class="planet-review">
      <div class="planet-img">
        <img
          :src="imagePaths.planet"
          v-if="showOverview || showGeology"
          alt="Planet Image"
          id="one"
        />

        <img
          :src="imagePaths.internal"
          v-if="showStructure"
          alt="Planet Internal Structure"
        />

        <img
          class="geology-img"
          :src="imagePaths.geology"
          v-if="showGeology"
          alt="Planet Geology"
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
import gsap from "gsap";
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
      imagePaths: {
        planet: "",
        internal: "",
        geology: "",
      },
    };
  },

  async created() {
    try {
      const planetImgModule = await import(
        `../assets/images/${this.planetImg}.svg`
      );
      const internalImgModule = await import(
        `../assets/images/${this.planetImg}-internal.svg`
      );
      const geologyImgModule = await import(
        `../assets/images/${this.planetImg}-geology.png`
      );

      this.imagePaths.planet = planetImgModule.default;
      this.imagePaths.internal = internalImgModule.default;
      this.imagePaths.geology = geologyImgModule.default;
    } catch (error) {
      console.error("Error loading images: ", error);
    }
  },

  methods: {
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
    animeImg() {
      gsap.fromTo(
        "#one",
        {},
        {
          scale: 1.1,
          duration: 1.5,
          ease: "power4.out",
        }
      );
    },
  },
  mounted() {
    this.animeImg();
  },
};
</script>

<style scoped lang="scss">
.planet-review {
  display: flex;
  justify-content: space-around;
  padding: 50px 250px;
  width: 100%;
  overflow: hidden;
  .planet-img {
    margin: auto;
    position: relative;
    img {
      max-width: 450px;
      &.geology-img {
        width: 199px;
        position: absolute;
        z-index: 3;
        right: 15%;
        top: 50%;
      }
    }
  }
}
.planet-resume {
  width: 350px;
  h2 {
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
    &:hover {
      background: #5e5e5e;
    }
    span {
      margin-right: 25px;
      font-family: "Spartan", sans-serif;
      font-size: 12px;
      line-height: 25px;
      letter-spacing: 2.57px;
      font-weight: bold;
      color: white;
    }
  }
}

.data-planet {
  display: flex;
  justify-content: space-around;
  padding: 0px 165px;
  margin-bottom: 50px;
  div {
    border: 1px solid var(--gray);
    width: 20%;
    padding: 21px 23px;
  }
  h4 {
    color: var(--white);
    line-height: 25px;
    letter-spacing: 1px;
    font-size: 11px;
    font-family: "Spartan", sans-serif;
    font-weight: bold;
    margin: 0;
  }
  span {
    font-family: "Antonio", sans-serif;
    color: var(--white);
    letter-spacing: -1.5px;
    font-size: 40px;
  }
}

/***___Media Queries___***/
/***___Tablet, Moins de 992px___***/

@media (max-width: 991.98px) {
  .planet-review {
    flex-direction: column;
    align-items: center;
    padding: 0px;
    margin-top: 30px;
    .planet-img {
      text-align: center;
      img {
        max-width: 80%;
        &.geology-img {
          top: 45%;
          left: 50%;
          width: 150px;
        }
      }
    }
    .planet-resume {
      .main-info {
        width: 300px;
        h2 {
          font-size: 48px;
        }
        .resume p {
          line-height: 22px;
          font-size: 11px;
        }
      }
      display: flex;
      align-items: center;
      justify-content: space-around;
      width: 100%;
    }
    .interaction-list {
      width: 300px;
      li {
        padding: 8px 20px;
        font-size: 9px;
        letter-spacing: 1.93px;
      }
    }
  }
  .data-planet {
    padding: 0px 40px;
    margin-top: 10px;
    div {
      padding: 16px 16px;
    }
    h4 {
      line-height: 16px;
      letter-spacing: 0.73px;
      font-size: 8px;
    }
    span {
      letter-spacing: -0.9px;
      font-size: 24px;
    }
  }
}
/***___Mobile, Moins de 668px___***/
@media (max-width: 667.98px) {
  .planet-img img {
    max-width: 50%;
    &.geology-img {
      width: 80px;
    }
  }
  .planet-resume {
    flex-direction: column-reverse;
    margin-top: 20px;
    h2 {
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
      span {
        display: none;
      }
    }
  }
  .data-planet {
    display: flex;
    flex-direction: column;
    padding: 0px 24px;
    div {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 9px 24px;
      margin: 4px 0px;
    }
    h4 {
      line-height: 16px;
      letter-spacing: 0.73px;
      font-size: 8px;
    }
    span {
      letter-spacing: -0.75px;
      font-size: 20px;
    }
  }
}
</style>
