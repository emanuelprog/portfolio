<template>
  <v-container>
    <v-row class="mt-12" ref="textRow">
      <v-col cols="12">
        <div class="text-center" ref="textDiv" v-if="loaded">
          <h2 class="fade-in">{{ language === 'pt' ? "OLÁ, SOU EMANUEL BESSA" : "HEY, I'M EMANUEL BESSA" }}</h2>
          <p class="smaller-paragraph fade-in">
            {{ language === 'pt' ? "Desenvolvedor full-stack fluente em Java/Spring (backend) e Angular/Vue (frontend). Sou especialista em criar experiências digitais perfeitas. Vamos colaborar e elevar o seu próximo projeto!" : "A full-stack developer fluent in Java/Spring (backend) and Angular/Vue (frontend). I specialize in crafting seamless digital experiences. Let's collaborate and elevate your next project!" }}
          </p>

          <div class="text-center mt-12 fade-in">
            <router-link to="/projects">
              <v-btn x-large color="amber darken-1" dark> {{ language === 'pt' ? 'PROJETOS' : 'PROJECTS' }} </v-btn>
            </router-link>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: ['language'],
  data() {
    return {
      loaded: false
    };
  },
  mounted() {
    setTimeout(() => {
      this.loaded = true;
    }, 500);
  },
};
</script>

<style scoped>
.fade-in {
  animation: fadeIn 1s ease-in-out forwards;
  opacity: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

h2 {
  color: black;
  margin-bottom: 0.5em;
  font-size: 60px;
  font-weight: 900;
}

@media screen and (max-width: 600px) {
  h2 {
    font-size: 3rem; /* Tamanho reduzido do texto para dispositivos móveis */
  }
}

p {
  color: black;
}

.smaller-paragraph {
  font-size: 0.9em;
  max-width: 600px;
  margin: 0 auto;
}
</style>