<template>
  <v-container class="text-center">
    <v-row class="mt-12 mb-4" ref="projectsRow">
      <v-col cols="12">
        <div class="text-center fade-in" ref="projectsDiv">
          <h2 class="fade-in">
            {{ language === "pt" ? "PROJETOS" : "PROJECTS" }}
          </h2>
          <div class="underline fade-in"></div>
          <p class="smaller-paragraph fade-in">
            {{
              language === "pt"
                ? "Aqui você encontrará alguns dos projetos pessoais e de clientes que criei, cada projeto contendo seus próprios detalhes"
                : "Here you will find some of the personal and clients projects that I created with each project containing its own case study"
            }}
          </p>
        </div>
      </v-col>
    </v-row>

    <v-divider class="mb-12 fade-in"></v-divider>

    <v-container fluid>
      <v-row class="mb-12 fade-in" v-for="(card, index) in cards" :key="index">
        <v-col cols="12" sm="6">
          <v-img
            :lazy-src="card.img"
            max-height="500"
            max-width="1000"
            :src="card.img"
          ></v-img>
        </v-col>
        <v-col cols="12" sm="6" style="text-align: left">
          <h1 class="fade-in">
            {{ language === "pt" ? card.titleBr : card.title }}
          </h1>
          <div class="fade-in">
            {{ language === "pt" ? card.messageBr : card.message }}
          </div>
          <div class="my-2 fade-in">
            <a :href="card.href">
              <v-btn color="amber darken-1" dark>{{
                language === "pt" ? "Ver mais" : "Case Study"
              }}</v-btn>
            </a>
            <a class="ml-5" :href="card.github">
              <v-icon
                dark
                size="28px"
                color="black"
                :title="language === 'pt' ? 'Abrir código' : 'Open source'"
              >
                mdi-github
              </v-icon>
            </a>
          </div>
        </v-col>
        <v-col cols="12">
        <div class="divider" v-if="index !== cards.length - 1"></div>
      </v-col>
      </v-row>
    </v-container>
  </v-container>
</template>

<script>
export default {
  props: ["language"],
  data() {
    return {
      loaded: false,
      cards: [
        {
          img: "/img/portfolio-mockup.png",
          titleBr: "Portfólio",
          title: "Portfolio",
          messageBr:
            "Conheça meu portfólio! Desenvolvido usando Vue.js com Vuetify, este projeto é um marco significativo em minha jornada. A versão 1.0 demonstra meu compromisso em combinar design elegante com funcionalidade poderosa. Mergulhe no meu trabalho e veja em primeira mão como transformo conceitos em realidade no mundo digital.",
          message:
            "Get to know my portfolio! Developed using Vue.js with Vuetify, this project marks a significant milestone in my journey. Version 1.0 showcases my commitment to blending stylish design with powerful functionality. Dive into my work and see firsthand how I transform concepts into reality in the digital realm.",
          github: "https://github.com/emanuelprog/portfolio",
          href: "https://portfolio-swart-one-23.vercel.app/",
        },
        {
          img: "/img/portal-professor-mockup.png",
          titleBr: "Portal do Professor",
          title: "Teacher Portal",
          messageBr:
            'Explore o meu "Portal do Professor"! Desenvolvido em Angular e Java, este projeto integra-se perfeitamente com APIs RESTful, incorporando uma mistura harmoniosa de sofisticação de front-end e robustez de back-end. Mergulhe para testemunhar como eu preencho a lacuna entre o design elegante e o gerenciamento eficiente de dados, capacitando educadores com ferramentas digitais intuitivas.',
          message:
            'Explore my "Teacher Portal"! Powered by Angular and Java, this project seamlessly integrates with RESTful APIs, embodying a harmonious blend of frontend sophistication and backend robustness. Dive in to witness how I bridge the gap between elegant design and efficient data handling, empowering educators with intuitive digital tools.',
          github: "https://github.com/emanuelprog",
          href: "https://portalreme.campogrande.ms.gov.br/home",
        },
        {
          img: "/img/crud-angular-spring-mockup.png",
          titleBr: "Cadastro de Clientes",
          title: "Customer Registration",
          messageBr:
            'O projeto consiste em um sistema CRUD para cadastro de clientes, desenvolvido com Angular no frontend e Spring Boot no backend. Utilizamos Angular para criar uma interface dinâmica que permite adicionar, editar, e excluir clientes, enquanto o Spring Boot fornece os endpoints para manipulação dos dados no backend. Essa combinação oferece uma solução eficiente e escalável para gerenciar informações de clientes.',
          message:
            'The project consists of a CRUD system for customer registration, developed with Angular on the frontend and Spring Boot on the backend. We used Angular to create a dynamic interface that allows adding, editing, and deleting customers, while Spring Boot provides the endpoints for data manipulation on the backend. This combination offers an efficient and scalable solution for managing customer information.',
          github: "https://github.com/emanuelprog/crud-angular-spring",
          href: "https://github.com/emanuelprog/crud-angular-spring",
        },
      ],
      mounted() {
        setTimeout(() => {
          this.loaded = true;
        }, 500);
      },
    };
  },
  created() {
    this.isMobile = this.$vuetify.breakpoint.smAndDown;
  },
};
</script>

<style>
.divider {
  width: 100%;
  height: 1px;
  background-color: rgba(0, 0, 0, 0.12);
  margin-top: 20px;
}
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
  font-size: 48px;
  font-weight: 700;
}

.underline {
  width: 40px;
  height: 5px;
  background-color: #ffb300;
  margin: 0 auto 20px;
  border-radius: 50px;
}

.transparent-card {
  background-color: transparent !important;
}
.mt-6 {
  margin-top: 6rem !important;
}
.smaller-paragraph {
  font-size: 1.1em;
  max-width: 800px;
  margin: 0 auto;
}
</style>