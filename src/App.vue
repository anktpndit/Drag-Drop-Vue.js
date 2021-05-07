<template>
  <v-app>
    <Header />
    <Body />
    <Footer />
  </v-app>
</template>

<script>
import Header from "./components/TheHeader";
import Body from "./components/TheBody";
import Footer from "./components/TheFooter";

export default {
  name: "App",

  components: {
    Header,
    Body,
    Footer,
  },

  data: () => ({
    //
  }),
};
</script>
