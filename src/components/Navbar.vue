<template>
  <div>
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-content>
            <v-list-item-title>{{
              language === "pt" ? item.titleBR : item.title
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="white">
      <v-app-bar-nav-icon
        class="d-lg-none"
        color="grey darken-4"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>

      <v-spacer class="d-lg-none"></v-spacer>

      <router-link to="/" class="ml-6 logo d-flex align-center">
        <v-avatar>
          <img src="/img/logo2.png" alt="John" />
        </v-avatar>
        <v-app-bar-title class="logo-text ml-3">EMANUEL BESSA</v-app-bar-title>
      </router-link>

      <v-spacer></v-spacer>

      <div class="d-none d-lg-block mr-12">
        <router-link
          to="/"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          {{ language === "pt" ? "INÍCIO" : "HOME" }}
        </router-link>
        <router-link
          to="/about"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          {{ language === "pt" ? "SOBRE" : "ABOUT" }}
        </router-link>
        <router-link
          to="/projects"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          {{ language === "pt" ? "PROJETOS" : "PROJECTS" }}
        </router-link>
      </div>
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-icon v-bind="attrs" v-on="on" size="24px" color="grey darken-4"
            >mdi-web</v-icon
          >
        </template>
        <v-list>
          <v-list-item
            v-for="(flag, index) in flags"
            :key="index"
            @click="onLanguageChanged(flag.language)"
          >
            <img :src="flag.src" width="18px" style="cursor: pointer" />
          </v-list-item>
        </v-list>
      </v-menu>
      <router-link
        to="/contact"
        class="ml-5"
        style="font-weight: bolder; font-size: 14px; text-decoration: none"
      >
        <v-btn outlined color="amber darken-1" class="d-none d-lg-block">
          {{ language === "pt" ? "CONTATO" : "CONTACT ME" }}
        </v-btn>
      </router-link>
    </v-app-bar>
  </div>
</template>

<script>
import { eventBus } from "@/event-bus.js";
import globals from "@/globals";

export default {
  created() {
    eventBus.$on("language-changed", this.onLanguageChanged);
  },
  destroyed() {
    eventBus.$off("language-changed", this.onLanguageChanged);
  },
  data() {
    return {
      drawer: false,
      items: [
        { title: "Home", titleBR: "Início", to: "/" },
        { title: "About", titleBR: "Sobre", to: "/about" },
        { title: "Projects", titleBR: "Projetos", to: "/projects" },
        { title: "Contact me", titleBR: "Contato", to: "/contact" },
      ],
      language: "en", // Assuming this is defined somewhere
      flags: [
        {
          src: "/img/brazil-flag-icon.png",
          language: "pt",
        },
        {
          src: "/img/united-states-flag-icon.png",
          language: "en",
        },
      ],
    };
  },
  methods: {
    onLanguageChanged(newLanguage) {
      this.language = newLanguage;
      globals.language = this.language;
      eventBus.$emit("languageChanged", this.language);
    },
  },
};
</script>

<style scoped>
.logo {
  display: flex;
  margin-right: 40px;
  text-decoration: none;
}

.logo-text {
  font-size: 16px;
  font-weight: 900;
  color: #212121;
}

.menuOpt {
  text-decoration: none;
  color: #212121;
}

.menuOpt:hover {
  color: #ffb300;
  cursor: pointer;
  transition: 0.3s;
}

.menuOpt.router-link-exact-active {
  color: #ffb300;
}
</style>