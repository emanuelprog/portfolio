<template>
  <v-app id="inspire" class="background">
    <Navbar />

    <v-main>
      <router-view :language="language"></router-view>
    </v-main>

    <Footer />
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";
import globals from "./globals.js";
import { eventBus } from "@/event-bus.js";

export default {
  mounted() {
    eventBus.$on("languageChanged", (newLinguagem) => {
      this.language = newLinguagem;
    });
  },
  components: {
    Navbar,
    Footer,
  },
  data: () => ({
    language: globals.language,
  }),
};
</script>

<style scoped>
.background {
  background-color: #f5f5f5;
  background-image: linear-gradient(to bottom, #ffffff, #cccccc);
}
</style>