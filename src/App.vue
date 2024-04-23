<template>
  <v-app id="inspire" class="background">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-content>
            <v-list-item-title>{{ language === 'pt' ? item.titleBR : item.title }}</v-list-item-title>
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
        <v-app-bar-title class="logo-texto ml-3">EMANUEL BESSA</v-app-bar-title>
      </router-link>

      <v-spacer></v-spacer>

      <div class="d-none d-lg-block mr-12">
        <router-link
          to="/"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          {{ language === 'pt' ? 'INÍCIO' : 'HOME' }}
        </router-link>
        <router-link
          to="/about"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          {{ language === 'pt' ? 'SOBRE' : 'ABOUT' }}
        </router-link>
        <router-link
          to="/projects"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          {{ language === 'pt' ? 'PROJETOS' : 'PROJECTS' }}
        </router-link>
      </div>
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-icon v-bind="attrs" v-on="on" size="24px" color="grey darken-4">mdi-web</v-icon>
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
           {{ language === 'pt' ? 'CONTATO' : 'CONTACT ME' }}
        </v-btn>
      </router-link>
    </v-app-bar>

    <v-main>
      <router-view :language="language"></router-view>
    </v-main>

    <v-footer color="grey darken-4">
      <v-card class="flex" color="grey darken-4">
        <v-card-title
          color="grey darken-4"
          style="color: white; justify-content: center"
        >
          <strong :style="{ fontSize: language === 'pt' ? '20px' : '18px' }"
            :class="{
              'subheading-mobile': $vuetify.breakpoint.smAndDown,
              subheading: !$vuetify.breakpoint.smAndDown,
            }"
          >
            {{ language === 'pt' ? 'Conecte-se comigo nas redes sociais!' : 'Get connected with me on social networks!' }}
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
  </v-app>
</template>

<script>
import { eventBus } from '@/event-bus.js';
export default {
  created() {
    // Assine o evento de mudança de idioma
    eventBus.$on('language-changed', this.onLanguageChanged);
  },
  destroyed() {
    // Lembre-se de cancelar a inscrição ao destruir o componente
    eventBus.$off('language-changed', this.onLanguageChanged);
  },
  data: () => ({
    drawer: false,
    items: [
      { title: "Home", titleBR: "Início", to: "/" },
      { title: "About", titleBR: "Sobre", to: "/about" },
      { title: "Projects", titleBR: "Projetos",  to: "/projects" },
      { title: "Contact me", titleBR: "Contato", to: "/contact" },
    ],
    flags: [
      {
        src: "/img/brazil-flag-icon.png", language: 'pt'
      },
      {
        src: "/img/united-states-flag-icon.png", language: 'en'
      },
    ],
    icons: ["mdi-github", "mdi-google", "mdi-linkedin", "mdi-instagram"],
    language: 'en', // Adicione a variável de idioma aqui
  }),
  methods: {
    getIconHref(icon) {
      // Implementação do método getIconHref...
    },
    onLanguageChanged(novoIdioma) {
      this.language = novoIdioma; // Correção aqui
    }
  },
};
</script>

<style scoped>
.background {
  background-color: #f5f5f5;
  background-image: linear-gradient(
    to bottom,
    #ffffff,
    #cccccc
  ); /* Gradient from white to gray */
}

.logo {
  display: flex;
  margin-right: 40px;
  text-decoration: none;
}

.logo-texto {
  font-size: 16px; /* Tamanho da fonte do texto */
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
  color: #ffb300; /* Cor do texto quando o link está ativo */
}

.subheading {
  font-size: 24px;
  /* Outros estilos */
}

.subheading-mobile {
  font-size: 18px;
}
</style>