<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
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

      <router-link to="/" class="mr-12 logo d-flex align-center">
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
          HOME
        </router-link>
        <router-link
          to="/about"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          ABOUT
        </router-link>
        <router-link
          to="/projects"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          PROJECTS
        </router-link>
      </div>
      <router-link
                to="/contact"
                style="font-weight: bolder; font-size: 14px; text-decoration: none;"
              >
      <v-btn outlined color="amber darken-1" class="d-none d-lg-block">
        CONTACT ME
      </v-btn>
      </router-link>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer color="grey darken-4">
      <v-card class="flex" color="grey darken-4">
        <v-card-title color="grey darken-4" style="color: white;">
          <strong :class="{ 'subheading-mobile': $vuetify.breakpoint.smAndDown, 'subheading': !$vuetify.breakpoint.smAndDown }">
            Get connected with us on social networks!
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
          &copy; {{ new Date().getFullYear() }} — <strong> Emanuel Bessa</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    items: [
      { title: "Home", to: "/" },
      { title: "About", to: "/about" },
      { title: "Projects", to: "/projects" },
      { title: "Contact me", to: "/contact" },
    ],
    icons: ["mdi-github", "mdi-google", "mdi-linkedin", "mdi-instagram"],
  }),
  methods: {
  getIconHref(icon) {
    switch (icon) {
      case 'mdi-github':
        return 'https://github.com/emanuelprog';
      case 'mdi-google':
        return 'https://www.google.com/';
      case 'mdi-linkedin':
        return 'https://www.linkedin.com/in/emanuel-bessa-65089b233?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app';
      case 'mdi-instagram':
        return 'https://www.instagram.com/emanuelfbessa';
      default:
        return '#';
    }
  }
}
};
</script>

<style scoped>
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
  font-size: 16px; /* Tamanho de fonte menor para dispositivos móveis */
  /* Outros estilos específicos para dispositivos móveis, se necessário */
}
</style>