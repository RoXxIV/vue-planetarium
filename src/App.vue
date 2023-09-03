<template>
  <div>
    <header>
      <router-link to="/"><span id="logo">THE PLANETS</span></router-link>
      <nav>
        <li><router-link to="/mercury">MERCURY</router-link></li>
        <li><router-link to="/venus">VENUS</router-link></li>
        <li><router-link to="/">EARTH</router-link></li>
        <li><router-link to="/mars">MARS</router-link></li>
        <li><router-link to="/jupiter">JUPITER</router-link></li>
        <li><router-link to="/saturn">SATURN</router-link></li>
        <li><router-link to="/uranus">URANUS</router-link></li>
        <li><router-link to="/neptune">NEPTUNE</router-link></li>
      </nav>
      <div id="menu-burger">
        <!-----Toggle Menu Burger Mobile----->
        <button
          id="btn-burger"
          class="menu cursorPointer"
          @click="
            ToggleBurgerMenu();
            showMobileMenu = !showMobileMenu;
          "
          aria-label="Main Menu"
        >
          <svg width="50" height="50" viewBox="0 0 100 100">
            <path
              class="line line1"
              d="M 20,29.000046 H 80.000231 C 80.000231,29.000046 94.498839,28.817352 94.532987,66.711331 94.543142,77.980673 90.966081,81.670246 85.259173,81.668997 79.552261,81.667751 75.000211,74.999942 75.000211,74.999942 L 25.000021,25.000058"
            />
            <path class="line line2" d="M 20,50 H 80" />
            <path
              class="line line3"
              d="M 20,70.999954 H 80.000231 C 80.000231,70.999954 94.498839,71.182648 94.532987,33.288669 94.543142,22.019327 90.966081,18.329754 85.259173,18.331003 79.552261,18.332249 75.000211,25.000058 75.000211,25.000058 L 25.000021,74.999942"
            />
          </svg>
        </button>
      </div>
    </header>
    <!-----Mobile Nav----->
    <transition name="fade">
      <div v-if="showMobileMenu" id="mobileNav">
        <ul>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="mercury" class="mobile-link">Mercury</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="venus" class="mobile-link">VENUS</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="/" class="mobile-link">EARTH</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="mars" class="mobile-link">MARS</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="jupiter" class="mobile-link">JUPITER</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="saturn" class="mobile-link">SATURN</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="uranus" class="mobile-link">URANUS</router-link>
          </li>
          <li
            @click="
              showMobileMenu = false;
              ToggleBurgerMenu();
            "
          >
            <span class="circle"></span
            ><router-link to="neptune" class="mobile-link">NEPTUNE</router-link>
          </li>
        </ul>
      </div>
    </transition>
    <main>
      <router-view v-slot="{ Component }">
        <transition name="scale" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>
    <!-----Footer----->
    <footer>
      <ul>
        <li>
          <a
            href="https://www.linkedin.com/in/evan-hermier-799b48121/"
            target="_blank"
          >
            <img
              class="buzz-out-on-hover"
              src="../src/assets/images/footer/1383262.png"
              alt="logo linkedin"
          /></a>
        </li>
        <li>
          <a href="https://github.com/RoXxIV" target="_blank">
            <img
              class="buzz-out-on-hover"
              src="../src/assets/images/footer/logo_github_icon_143196.png"
              alt="logo github"
          /></a>
        </li>
        <li>
          <a href="https://codepen.io/RoXx" target="_blank">
            <img
              class="buzz-out-on-hover"
              src="../src/assets/images/footer/free-codepen-3771364-3149472.png"
              alt="logo codepen"
          /></a>
        </li>
        <li>
          <a href="https://www.freecodecamp.org/roxxx" target="_blank">
            <img
              class="buzz-out-on-hover"
              src="../src/assets/images/footer/Microsoft.VisualStudio.Services.Icons.png"
              alt="freecodecamp"
          /></a>
        </li>
      </ul>
    </footer>
  </div>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
import gsap from "gsap";

export default {
  name: "App",

  data() {
    return {
      showMobileMenu: false,
    };
  },
  methods: {
    ToggleBurgerMenu() {
      const burger = document.getElementById("btn-burger");
      burger.classList.toggle("opened");
      burger.setAttribute("aria-expanded", burger.classList.contains("opened"));
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 24px 0px;
  border-bottom: 1px solid #979797;
  #logo {
    font-family: "Antonio", sans-serif;
    font-size: 28px;
    color: var(--white);
    margin-left: 32px;
  }
  nav {
    display: flex;
    justify-content: space-around;
    width: 665px;
    margin-right: 40px;

    li {
      color: var(--white);
      line-height: 25px;
      font-size: 11px;
      font-family: "Spartan", sans-serif;
      letter-spacing: 1px;
      font-weight: bold;
    }
  }
}
/***___Media Queries___***/
/***___Tablet, Moins de 992px___***/
@media (max-width: 991.98px) {
  header {
    flex-direction: column;
    padding: 0px 0px 24px 0px;
    #logo {
      margin: 32px auto;
    }
    nav {
      margin-top: 3px;
    }
  }
}
/***___Mobile, Moins de 668px___***/
@media (max-width: 667.98px) {
  header {
    flex-direction: row;
    justify-content: space-between;
    padding: 16px 0px;
    position: relative;
    #logo {
      margin: 0px 0px 0px 24px;
    }
    nav {
      display: none;
    }
    #menu-burger {
      display: block;
      margin-right: 24px;
    }
  }
}
/***___Mobile Nav___***/
#mobileNav {
  position: absolute;
  width: 100%;
  font-size: 1.3em;
  z-index: 4;
  ul {
    margin: 0;
    padding-top: 20px;
    background: var(--dark-blue);
    li {
      display: flex;
      align-items: center;
      margin: 0px 24px;
      padding: 20px 0px;
      border-bottom: 1px solid #979797;
    }
    .mobile-link {
      color: var(--white);
      line-height: 25px;
      font-size: 15px;
      font-family: "Spartan", sans-serif;
      letter-spacing: 1.36px;
      font-weight: bold;
    }
  }
}
.circle {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin-right: 25px;
}
$colors: (
  #def4fc,
  #f7cc7f,
  #545bfe,
  #ff6a45,
  #ecad7a,
  #fccb6b,
  #65f0d5,
  #497efa
);
@for $i from 1 through length($colors) {
  li:nth-child(0n + #{$i}) span {
    background: nth($colors, $i);
  }
}
/**Transition */
.fade-enter-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
/***___Button Burger + Animation___***/
#menu-burger {
  display: none;
  .menu {
    background-color: transparent;
    border: none;
    display: flex;
    padding: 0;
  }
}
.line {
  fill: none;
  stroke: #979797;
  stroke-width: 6;
  transition: stroke-dasharray 600ms cubic-bezier(0.4, 0, 0.2, 1),
    stroke-dashoffset 600ms cubic-bezier(0.4, 0, 0.2, 1);
}
.line1 {
  stroke-dasharray: 60 207;
  stroke-width: 6;
}
.line2 {
  stroke-dasharray: 60 60;
  stroke-width: 6;
}
.line3 {
  stroke-dasharray: 60 207;
  stroke-width: 6;
}
.opened .line1 {
  stroke-dasharray: 90 207;
  stroke-dashoffset: -134;
  stroke-width: 6;
}
.opened .line2 {
  stroke-dasharray: 1 60;
  stroke-dashoffset: -30;
  stroke-width: 6;
}
.opened .line3 {
  stroke-dasharray: 90 207;
  stroke-dashoffset: -134;
  stroke-width: 6;
}
/**router-view transition */
.scale-enter-active,
.scale-leave-active {
  transition: all 0.5s ease;
}

.scale-enter-from,
.scale-leave-to {
  opacity: 0;
  transform: scale(0.9);
}
/***___Footer___***/
footer {
  padding: 15px;
  border-top: 1px solid #979797;
  text-align: center;
  margin-top: 100px;
  ul {
    display: flex;
    justify-content: center;
  }
  img {
    max-width: 35px;
    margin: 0px 15px;
  }
}
@-webkit-keyframes buzz-out-on-hover {
  10% {
    -webkit-transform: translateX(3px) rotate(2deg);
    transform: translateX(3px) rotate(2deg);
  }
  20% {
    -webkit-transform: translateX(-3px) rotate(-2deg);
    transform: translateX(-3px) rotate(-2deg);
  }
  30% {
    -webkit-transform: translateX(3px) rotate(2deg);
    transform: translateX(3px) rotate(2deg);
  }
  40% {
    -webkit-transform: translateX(-3px) rotate(-2deg);
    transform: translateX(-3px) rotate(-2deg);
  }
  50% {
    -webkit-transform: translateX(2px) rotate(1deg);
    transform: translateX(2px) rotate(1deg);
  }
  60% {
    -webkit-transform: translateX(-2px) rotate(-1deg);
    transform: translateX(-2px) rotate(-1deg);
  }
  70% {
    -webkit-transform: translateX(2px) rotate(1deg);
    transform: translateX(2px) rotate(1deg);
  }
  80% {
    -webkit-transform: translateX(-2px) rotate(-1deg);
    transform: translateX(-2px) rotate(-1deg);
  }
  90% {
    -webkit-transform: translateX(1px) rotate(0);
    transform: translateX(1px) rotate(0);
  }
  100% {
    -webkit-transform: translateX(-1px) rotate(0);
    transform: translateX(-1px) rotate(0);
  }
}
@keyframes buzz-out-on-hover {
  10% {
    -webkit-transform: translateX(3px) rotate(2deg);
    transform: translateX(3px) rotate(2deg);
  }
  20% {
    -webkit-transform: translateX(-3px) rotate(-2deg);
    transform: translateX(-3px) rotate(-2deg);
  }
  30% {
    -webkit-transform: translateX(3px) rotate(2deg);
    transform: translateX(3px) rotate(2deg);
  }
  40% {
    -webkit-transform: translateX(-3px) rotate(-2deg);
    transform: translateX(-3px) rotate(-2deg);
  }
  50% {
    -webkit-transform: translateX(2px) rotate(1deg);
    transform: translateX(2px) rotate(1deg);
  }
  60% {
    -webkit-transform: translateX(-2px) rotate(-1deg);
    transform: translateX(-2px) rotate(-1deg);
  }
  70% {
    -webkit-transform: translateX(2px) rotate(1deg);
    transform: translateX(2px) rotate(1deg);
  }
  80% {
    -webkit-transform: translateX(-2px) rotate(-1deg);
    transform: translateX(-2px) rotate(-1deg);
  }
  90% {
    -webkit-transform: translateX(1px) rotate(0);
    transform: translateX(1px) rotate(0);
  }
  100% {
    -webkit-transform: translateX(-1px) rotate(0);
    transform: translateX(-1px) rotate(0);
  }
}
.buzz-out-on-hover {
  display: inline-block;
  vertical-align: middle;
  -webkit-transform: perspective(1px) translateZ(0);
  transform: perspective(1px) translateZ(0);
  box-shadow: 0 0 1px rgba(0, 0, 0, 0);
}
.buzz-out-on-hover:hover,
.buzz-out-on-hover:focus,
.buzz-out-on-hover:active {
  -webkit-animation-name: buzz-out-on-hover;
  animation-name: buzz-out-on-hover;
  -webkit-animation-duration: 0.75s;
  animation-duration: 0.75s;
  -webkit-animation-timing-function: linear;
  animation-timing-function: linear;
  -webkit-animation-iteration-count: 1;
  animation-iteration-count: 1;
}
</style>
