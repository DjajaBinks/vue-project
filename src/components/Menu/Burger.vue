<template>
  <div id="burger" :class="{ 'active' : isBurgerActive }" @click.prevent="toggle">
    <slot>
      <button type="button" class="burger-button" title="Menu">
        <span class="burger-bar burger-bar--1"></span>
        <span class="burger-bar burger-bar--2"></span>
        <span class="burger-bar burger-bar--3"></span>
      </button>
    </slot>
  </div>
</template>
<script>
import { store, mutations } from "@/store.js";

export default {
  computed: {
    isBurgerActive() {
      return store.isNavOpen;
    }
  },
  methods: {
    toggle() {
      mutations.toggleNav();
    }
  }
};
</script>
<style>
.hidden {
  visibility: hidden;
}

button {
  cursor: pointer;
}

button:focus {
  outline: 0;
}
.burger-button {
  position: relative;
  height: 30px;
  width: 32px;
  display: block;
  /* z-index: 999; */
  border: 0;
  border-radius: 0;
  /* background-color: green; */
  background-color: transparent;
  pointer-events: all;
  transition: transform 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
  margin-right: 10px;
}

.burger-bar {
  background-color: #130f40;
  position: absolute;
  top: 50%;
  right: 6px;
  left: 6px;
  height: 2px;
  width: auto;
  transition: transform 0.6s cubic-bezier(0.165, 0.84, 0.44, 1),
    opacity 0.3s cubic-bezier(0.165, 0.84, 0.44, 1),
    background-color 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
}

.burger-bar--1 {
  -webkit-transform: translateY(-6px);
  transform: translateY(-6px);
}

.burger-bar--2 {
  transform-origin: 0% 100%;
  transform: scaleX(0.8);
}

.burger-button:hover .burger-bar--2 {
  transform: scaleX(1);
}

.no-touchevents .burger-bar--2:hover {
  transform: scaleX(1);
}

.burger-bar--3 {
  transform: translateY(6px);
}

#burger.active .burger-button {
  /* transform: rotate(-180deg);*/
  z-index: 999;
  margin-left: 250px;
  transform: rotate(90deg);
}

#burger.active .burger-bar {
  background-color: #fff;
}

#burger.active .burger-bar--1 {
  /* transform: rotate(45deg); */
  left:3px;
  top: 12px;
  width: 30px;
  transition: .3s cubic-bezier(.8, .5, .2, 1.4);
  transform: rotate(90deg);
  transition-delay: 150ms;
}

#burger.active .burger-bar--2 {
  /* opacity: 0; */
  left:3px;
  top: 12px;
  width: 20px;
  transition: .3s cubic-bezier(.8, .5, .2, 1.4);
  transform: rotate(45deg);
  transition-delay: 50ms;
}

#burger.active .burger-bar--3 {
  /* transform: rotate(-45deg); */
  left:14px;
  top: 20px;
  width: 20px;
  transition: .3s cubic-bezier(.8, .5, .2, 1.4);
  transform: rotate(-45deg);
  transition-delay: 100ms;
}
</style>
