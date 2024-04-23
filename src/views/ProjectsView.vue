<template>
  <v-container class="text-center">

  <v-row class="mt-12 mb-4">
      <v-col cols="12">
        <div class="text-center">
          <h2>PROJECTS</h2>
          <div class="underline"></div>
          <p class="smaller-paragraph">
            Here you will find some of the personal and clients projects that I created with each project containing its own case study
          </p>
        </div>
      </v-col>
    </v-row>

    <v-divider class="mb-12"></v-divider>

      <v-container fluid>
    <v-row class="mb-12">
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
        <h1>Portfólio</h1>
        <div>Get to know my portfolio! Developed using Vue.js with Vuetify, this project marks a significant milestone in my journey. Version 1.0 showcases my commitment to blending stylish design with powerful functionality. Dive into my work and see firsthand how I transform concepts into reality in the digital realm.</div>
        <div class="my-2">
          <a href="https://portfolio-swart-one-23.vercel.app/"><v-btn
            color="amber darken-1"
            dark
          >
            Case Study
          </v-btn></a>
        </div>
      </v-col>
    </v-row>
    <v-divider class="mb-12"></v-divider>
    <v-row class="mb-12">
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
        <h1>Portal do Professor</h1>
        <div>Explore my "Portal do Professor"! Powered by Angular and Java, this project seamlessly integrates with RESTful APIs, embodying a harmonious blend of frontend sophistication and backend robustness. Dive in to witness how I bridge the gap between elegant design and efficient data handling, empowering educators with intuitive digital tools.</div>
        <div class="my-2">
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
      isMobile: false,
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
    };
  },
  created() {
    this.isMobile = this.$vuetify.breakpoint.smAndDown; 
  }
};
</script>

<style>
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