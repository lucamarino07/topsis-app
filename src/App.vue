<template>
  <v-ons-page id="app">
    <div class="background"></div>
    <v-ons-splitter>
      <v-ons-splitter-side
        swipeable
        collapse
        width="250px"
        :animation="$ons.platform.isAndroid() ? 'overlay' : 'reveal'"
        :open.sync="menuIsOpen"
      >
        <menu-page></menu-page>
      </v-ons-splitter-side>

      <v-ons-splitter-content>
        <home-page @toggleMenu="menuIsOpen = !menuIsOpen"></home-page>
      </v-ons-splitter-content>
    </v-ons-splitter>
  </v-ons-page>
</template>

<script>
import HomePage from "./components/HomePage";
import MenuPage from "./components/MenuPage";

export default {
  name: "app",
  data() {
    return {
      menuIsOpen: false
    };
  },
  components: {
    HomePage,
    MenuPage
  },
  beforeMount() {
    const html = document.documentElement;
    if (this.$ons.platform.isIPhoneX()) {
      html.setAttribute("onsflag-iphonex-portrait", "");
      html.setAttribute("onsflag-iphonex-landscape", "");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ons-splitter-side[side="left"][animation="overlay"] {
  border-right: 1px solid #bbb;
}

.page__background {
  background-color: black;
}
</style>
