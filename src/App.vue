<template>
  <div id="app">
    <header>
      <Header />
    </header>
    <main>
      <Main />
    </main>
    
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
};
</script>

<style>
@import './style/variables.scss';
@import './style/general.scss';
@import './style/common.scss';


</style>
