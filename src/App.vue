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
          to="/experiences"
          class="mr-12 menuOpt"
          style="font-weight: bolder; font-size: 14px"
        >
          EXPERIENCES</router-link
        >
      </div>

      <v-btn outlined color="amber darken-1" class="d-none d-lg-block">
        CONTACT ME
      </v-btn>
    </v-app-bar>

    <v-main style="background-color: #f5f5f5">
      <router-view></router-view>
    </v-main>

    

    <v-footer color="grey darken-4" padless>
      <v-card class="flex" color="grey darken-4">
        <v-card-title color="grey darken-4" style="color: white">
          <strong class="subheading"
            >Get connected with us on social networks!</strong
          >

          <v-spacer></v-spacer>

          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4"
            color="white"
            icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-title>

        <v-card-text class="py-2 text-center" style="color: white">
          {{ new Date().getFullYear() }} — <strong>&copy; Emanuel Bessa</strong>
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
      { title: "Experiences", to: "/experiences" },
      { title: "Projects", to: "/projects" },
      { title: "Contact me", to: "/contact" },
    ],
    icons: ["mdi-github", "mdi-google", "mdi-linkedin", "mdi-instagram"],
  }),
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
</style>