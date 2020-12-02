<template>
  <div class="sidebar-backdrop" v-if="isPanelOpen">
      <transition name="slide">
        <div v-if="isPanelOpen" class="sidebar-panel">
          <slot>
            <b-menu>
              <b-menu-list label="You're logged in as: User">
                <b-menu-item icon="information-outline" label="Info"></b-menu-item>
                <b-menu-item icon="settings" :active="isActive" expanded>
                  <template slot="label" slot-scope="props">
                    Administrator
                    <b-icon class="is-pulled-right" :icon="props.expanded ? 'menu-down' : 'menu-up'"></b-icon>
                  </template>
                  <b-menu-item icon="account" label="Users"></b-menu-item>
                  <b-menu-item icon="cellphone-link">
                    <template slot="label">
                      Devices
                      <b-dropdown aria-role="list" class="is-pulled-right" position="is-bottom-left">
                        <b-icon icon="dots-vertical" slot="trigger"></b-icon>
                        <b-dropdown-item aria-role="listitem">Action</b-dropdown-item>
                        <b-dropdown-item aria-role="listitem">Another action</b-dropdown-item>
                        <b-dropdown-item aria-role="listitem">Something else</b-dropdown-item>
                      </b-dropdown>
                    </template>
                  </b-menu-item>
                  <b-menu-item icon="cash-multiple" label="Payments" disabled></b-menu-item>
                </b-menu-item>
                <b-menu-item icon="account" label="My Account">
                  <b-menu-item label="Account data"></b-menu-item>
                  <b-menu-item label="Addresses"></b-menu-item>
                </b-menu-item>
              </b-menu-list>
              <b-menu-list>
                <b-menu-item label="Expo" icon="link" tag="router-link" target="_blank" to="/expo"></b-menu-item>
              </b-menu-list>
              <b-menu-list label="Actions">
                <b-menu-item label="Logout"></b-menu-item>
              </b-menu-list>
            </b-menu>
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
    },
  data() {
    return {
      isActive: true
    }
  }
}
</script>
<style>
div.menu{
  width: 200px;
  background: #fff;
}
    .slide-enter-active,
    .slide-leave-active
    {
        transition: transform 0.2s ease;
    }

    .slide-enter,
    .slide-leave-to {
        transform: translateX(100%);
        transition: all 200ms ease-in 2s
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
        width: 250px;
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
