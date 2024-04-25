<template>
  <v-footer color="grey darken-4">
    <v-card class="flex" color="grey darken-4">
      <v-card-title
        color="grey darken-4"
        style="color: white; justify-content: center"
      >
        <strong
          :style="{ fontSize: language === 'pt' ? '20px' : '18px' }"
          :class="{
            'subheading-mobile': $vuetify.breakpoint.smAndDown,
            subheading: !$vuetify.breakpoint.smAndDown,
          }"
        >
          {{
            language === "pt"
              ? "Conecte-se comigo nas redes sociais!"
              : "Get connected with me on social networks!"
          }}
        </strong>

        <v-spacer></v-spacer>

        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4"
          color="white"
          icon
        >
          <a :href="getIconHref(icon)" target="_blank" style="color: white">
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </a>
        </v-btn>
      </v-card-title>

      <v-card-text class="py-2 text-center" style="color: white">
        &copy; {{ new Date().getFullYear() }} —
        <strong> Emanuel Bessa</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
import { eventBus } from "@/event-bus.js";
import globals from "@/globals";
export default {
  mounted() {
    eventBus.$on("languageChanged", (newLinguagem) => {
      this.language = newLinguagem;
    });
  },
  data: () => ({
    icons: ["mdi-github", "mdi-google", "mdi-linkedin", "mdi-instagram"],
    language: globals.language,
  }),
  methods: {
    getIconHref(icon) {
      switch (icon) {
        case "mdi-github":
          return "https://github.com/emanuelprog";
        case "mdi-google":
          return "https://www.google.com/";
        case "mdi-linkedin":
          return "https://www.linkedin.com/in/emanuel-bessa-65089b233?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app";
        case "mdi-instagram":
          return "https://www.instagram.com/emanuelfbessa";
        default:
          return "#";
      }
    },
  },
};
</script>

<style scoped>
.subheading {
  font-size: 24px;
  /* Outros estilos */
}

.subheading-mobile {
  font-size: 18px;
}
</style>