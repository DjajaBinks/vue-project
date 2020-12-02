<template>
  <div id="app">
    <nav class="main-nav">
      <Menu/>
      <h1 class="title nav">Company</h1>
      <Burger/>
    </nav>
    <Content/>
    <Footer/>
  </div>
</template>

<script>
import Menu from "./components/Menu.vue";
import Burger from "./components/Menu/Burger.vue";
import Content from "./components/Content.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "app",
  components: {
    Menu,
    Burger,
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
h1.title.nav{
  line-height: 1.5rem;
  margin-bottom: 10px;
  height: 28px;
  position: absolute;
  padding-left: 40px;
}

section.hero{
  margin-top: 10px;
}
</style>
