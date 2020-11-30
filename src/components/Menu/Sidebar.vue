<template>
    <div class="sidebar">
        <div class="sidebar-backdrop" @click="closeSidebarPanel" v-if="isPanelOpen"></div>
        <transition name="slide">
            <div v-if="isPanelOpen"
                 class="sidebar-panel">
                <slot>
                  <ul class="sidebar-panel-nav">
                    <h1 class="title has-background">Hello User</h1>
                      <li>
                        <a href="#home">
                        <span class="effect-underline">Home</span>
                        </a>
                      </li>
                      <li>
                        <a href="#about" class="effect-underline">
                          <span class="effect-underline">About</span>
                        </a>
                      </li>
                      <li>
                        <a href="#contact" class="effect-underline">
                          <span class="effect-underline">Contact</span>
                        </a>
                      </li>
                  </ul>
                </slot>
            </div>
        </transition>
    </div>
</template>
<script>
import { store, mutations } from '@/store.js';

    export default {
        methods: {
            closeSidebarPanel: mutations.toggleNav
        },
        computed: {
            isPanelOpen() {
                return store.isNavOpen
            }
        }
    }
</script>
<style>
    .slide-enter-active,
    .slide-leave-active
    {
        transition: transform 0.2s ease;
    }

    .slide-enter,
    .slide-leave-to {
        transform: translateX(-100%);
        transition: all 150ms ease-in 0s
    }

    .sidebar-backdrop {
        background-color: rgba(19, 15, 64, .5);
        width: 100vw;
        height: 100vh;
        position: fixed;
        top: 0;
        left: 0;
        cursor: pointer;
        z-index: 1;
    }

    .sidebar-panel {
        overflow-y: auto;
        background-color: #fff;
        position: fixed;
        left: 0;
        top: 0;
        height: 100vh;
        z-index: 999;
        padding: 1rem 20px 2rem 20px;
        width: 300px;
    }

    ul.sidebar-panel-nav {
      list-style-type: none;
    }
    ul.sidebar-panel-nav > li > a {
      width: 200px;
      color: #000;
      text-decoration: none;
      font-size: 1.5rem;
      display: block;
      padding-bottom: 0.5em;
    }
    span{
      position: relative;
      display: inline-block;
    }
    span.effect-underline:after {
      content: '';
      position: absolute;
      left: 0;
      display: inline-block;
      height: 1em;
      width: 100%;
      border-bottom: 1px solid;
      margin-top: 10px;
      opacity: 0;
      -webkit-transition: opacity 0.35s, -webkit-transform 0.35s;
      transition: opacity 0.35s, transform 0.35s;
      -webkit-transform: scale(0,1);
      transform: scale(0,1);
      transform-origin: left;
    }

    span.effect-underline:hover:after {
      opacity: 1;
      -webkit-transform: scale(1);
      transform: scale(1);
    }
    h1.title {
      line-height: 25px;
    }
    .has-background{
      background: red;
    }
</style>
