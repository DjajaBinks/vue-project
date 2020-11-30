<template>
  <div id="app">
    <nav class="main-nav">
      <Burger></Burger>
      <h1 class="title">Djaja</h1>
      <Sidebar/>
    </nav>
    <Content/>
    <Footer/>
  </div>
</template>

<script>
import Burger from "./components/Menu/Burger.vue";
import Sidebar from "./components/Menu/Sidebar.vue";
import Content from "./components/Content.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "app",
  components: {
    Burger,
    Sidebar,
    Content,
    Footer
  }
};
</script>
<style>
html {
  height: 100%;
  overflow: hidden;
}
body {
  border: 0;
  margin: 0;
  padding: 0;
  height: 100%;
}
.main-nav {
  display: flex;
  padding: 0.5rem 0.5rem 0;
}
</style>
