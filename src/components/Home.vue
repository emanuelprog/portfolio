<template>
  <v-container>
    <v-row class="mt-12" ref="textRow">
      <v-col cols="12">
        <div class="text-center" ref="textDiv" v-if="loaded">
          <h2 class="fade-in">HEY, I'M EMANUEL BESSA</h2>
          <p class="smaller-paragraph fade-in">
            A full-stack developer fluent in Java/Spring (backend) and
            Angular/Vue (frontend). I specialize in crafting seamless digital
            experiences. Let's collaborate and elevate your next project!
          </p>

          <div class="text-center mt-12 fade-in">
            <router-link to="/projects">
              <v-btn x-large color="amber darken-1" dark> PROJECTS </v-btn>
            </router-link>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      loaded: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.loaded = true;
    }, 500); // Tempo para a animação começar após o carregamento da página
  },
};
</script>

<style scoped>
.fade-in {
  animation: fadeIn 1s ease-in-out forwards; /* forwards mantém o estado final da animação */
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

p {
  color: black;
}

.smaller-paragraph {
  font-size: 0.9em; /* Define um tamanho de fonte menor para o parágrafo */
  max-width: 600px; /* Define uma largura máxima para o parágrafo */
  margin: 0 auto; /* Centraliza o parágrafo horizontalmente */
}
</style>