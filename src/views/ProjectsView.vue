<template>
  <v-container class="text-center">
    <v-row class="mt-12 mb-4" ref="projectsRow">
      <v-col cols="12">
        <div class="text-center" ref="projectsDiv" v-if="loaded">
          <h2 class="fade-in">PROJECTS</h2>
          <div class="underline fade-in"></div>
          <p class="smaller-paragraph fade-in">
            Here you will find some of the personal and clients projects that I created with each project containing its own case study
          </p>
        </div>
      </v-col>
    </v-row>

    <v-divider class="mb-12 fade-in"></v-divider>

    <v-container fluid>
      <v-row class="mb-12 fade-in">
        <!-- Primeira coluna -->
        <v-col cols="12" sm="6">
          <v-img
            lazy-src="/img/mockup1.png"
            max-height="500"
            max-width="1000"
            src="/img/mockup1.png"
          ></v-img>
        </v-col>
        <!-- Segunda coluna -->
        <v-col cols="12" sm="6" style="text-align: left">
          <h1 class="fade-in">Portfólio</h1>
          <div class="fade-in">Get to know my portfolio! Developed using Vue.js with Vuetify, this project marks a significant milestone in my journey. Version 1.0 showcases my commitment to blending stylish design with powerful functionality. Dive into my work and see firsthand how I transform concepts into reality in the digital realm.</div>
          <div class="my-2 fade-in">
            <a href="https://portfolio-swart-one-23.vercel.app/"><v-btn
              color="amber darken-1"
              dark
            >
              Case Study
            </v-btn></a>
          </div>
        </v-col>
      </v-row>
      <v-divider class="mb-12 fade-in"></v-divider>
      <v-row class="mb-12 fade-in">
        <!-- Terceira coluna -->
        <v-col cols="12" sm="6">
          <v-img
            lazy-src="/img/mockup2.png"
            max-height="500"
            max-width="1000"
            src="/img/mockup2.png"
          ></v-img>
        </v-col>
        <!-- Quarta coluna -->
        <v-col cols="12" sm="6" style="text-align: left">
          <h1 class="fade-in">Portal do Professor</h1>
          <div class="fade-in">Explore my "Portal do Professor"! Powered by Angular and Java, this project seamlessly integrates with RESTful APIs, embodying a harmonious blend of frontend sophistication and backend robustness. Dive in to witness how I bridge the gap between elegant design and efficient data handling, empowering educators with intuitive digital tools.</div>
          <div class="my-2 fade-in">
            <a href="https://portalreme.campogrande.ms.gov.br/home"><v-btn
              color="amber darken-1"
              dark
            >
              Case Study
            </v-btn></a>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      loaded: false,
      cards: [
        { 
          title: 'Portal do Professor (Angular + Java)', 
          src: '/img/portal-professor.png', 
          flex: 6,
          images: [
            { src: '/img/portal-professor.png' },
            { src: '/img/portal-professor-code.png' }
          ],
        },
        { 
          title: 'Portfólio v1.0 (Vue + Vuetify)', 
          src: '/img/portfolio.png', 
          flex: 6,
          images: [
            { src: '/img/portfolio.png' },
            { src: '/img/portfolio-code.png' },
          ],
        },
        // Adicione mais conjuntos de imagens conforme necessário
      ],
      mounted() {
    setTimeout(() => {
      this.loaded = true;
    }, 500); // Tempo para a animação começar após o carregamento da página
  },
    };
  },
  created() {
    this.isMobile = this.$vuetify.breakpoint.smAndDown; 
  }
};
</script>

<style>
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
  font-size: 48px;
  font-weight: 700;
}

.underline {
  width: 40px; /* Defina a largura da borda */
  height: 5px; /* Defina a altura da borda */
  background-color: #ffb300; /* Cor da borda */
  margin: 0 auto 20px; /* Margem para centralizar e espaçar do texto */
  border-radius: 50px;
}

.transparent-card {
  background-color: transparent !important;
}
.mt-6 {
  margin-top: 6rem !important;
}
.smaller-paragraph {
  font-size: 1.1em; /* Define um tamanho de fonte menor para o parágrafo */
  max-width: 800px; /* Define uma largura máxima para o parágrafo */
  margin: 0 auto; /* Centraliza o parágrafo horizontalmente */
}
</style>