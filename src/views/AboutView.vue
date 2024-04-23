<template>
  <v-container>
    <v-row class="mt-12 mb-4 fade-in">
      <!-- Adicionando uma margem inferior menor -->
      <v-col cols="12">
        <div class="text-center">
          <h2>{{ language === 'pt' ? 'SOBRE MIM' : 'ABOUT ME' }}</h2>
          <div class="underline"></div>
          <p class="smaller-paragraph">
            {{ language === 'pt' ? 'Aqui você encontrará mais informações sobre mim, o que faço e minhas habilidades atuais principalmente em termos de programação e tecnologia' : 'Here you will find more information about me, what I do, and my current skills mostly in terms of programming and technology' }}
          </p>
        </div>
      </v-col>
    </v-row>

    <v-divider class="mb-12 fade-in"></v-divider>


    <v-row class="mt-4 fade-in">
      <v-col cols="12" sm="8" md="6">
        <div class="d-flex justify-center align-center" style="height: 100%;">
            <img src="/img/logo-about3.jpg" style="width: 330px; height: 330px; border-radius: 50%; object-fit: cover;">
        </div>
      </v-col>
      <v-col cols="12" sm="8" md="6">
        <div class="text-center">
          <h1 :class="{ 'text-mobile': $vuetify.breakpoint.smAndDown, 'text-pc': !$vuetify.breakpoint.smAndDown }">{{ language === 'pt' ? 'Me conheça!' : 'Get to know me!' }}</h1>
          <p>
            {{ language === 'pt' ? 'Emanuel Fernandes Bessa, 23 anos, é um apaixonado programador nascido em Boston, EUA, mas criado em Minas Gerais e posteriormente mudou-se para Campo Grande. Sua determinação em revolucionar a área da programação com suas ideias criativas é evidente em seu trabalho. Ele busca constantemente maneiras de inovar e aprimorar suas habilidades, demonstrando uma sede insaciável de aprendizado e um espírito colaborativo. Sua ambição e entusiasmo tornam-no uma presença inspiradora na comunidade de desenvolvimento de software.' : "Emanuel Fernandes Bessa, 23 years old, is a passionate programmer born in Boston, USA, but raised in Minas Gerais and later moved to Campo Grande. His determination to revolutionize the field of programming with his creative ideas is evident in his work. He constantly seeks ways to innovate and improve his skills, demonstrating an insatiable thirst for learning and a collaborative spirit. His ambition and enthusiasm make him an inspiring presence in the software development community." }}
          </p>
        </div>
      </v-col>
    </v-row>

    <v-divider class="mt-12 fade-in"></v-divider>

    <v-row class="mt-4 fade-in">
      <v-col cols="12" class="mb-12">
        <div class="text-center">
          <h1 :class="{ 'text-mobile': $vuetify.breakpoint.smAndDown, 'text-pc': !$vuetify.breakpoint.smAndDown }">{{ language === 'pt' ? 'Meus Conhecimentos!' : 'My Skills!' }}</h1>
          <div class="buttons">
             <v-btn
                v-for="(icon, index) in iconList"
                :key="index"
                color="amber darken-1"
                dark
                class="ml-2 mt-2"
              >
                <v-icon>{{ icon.name }}</v-icon> {{icon.title}}
              </v-btn>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: ['language'],
  name: "AboutMe",
  data() {
    return {
      iconList: [
        { name: 'mdi-language-java', title: 'Java' },
        { name: 'mdi-power', title: 'Spring Boot' },
        { name: 'mdi-language-javascript', title: 'Javascript' },
        { name: 'mdi-language-typescript', title: 'TypeScript' },
        { name: 'mdi-angular', title: 'Angular' },
        { name: 'mdi-alpha-z-box', title: 'ZK FRAMEWORK' },
        { name: 'mdi-vuejs', title: 'Vue.js' }
      ] // Lista de ícones com título
    };
  },
  mounted() {
    this.$nextTick(() => {
      const elements = document.querySelectorAll(".fade-in");
      elements.forEach((element) => {
        element.style.opacity = 1;
      });
    });
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

.text-mobile {
  font-size: 22px;
  color: black;
}

.text-pc {
  font-size: 42px;
  color: black;
}

p {
  color: black;
}

.smaller-paragraph {
  font-size: 1.1em; /* Define um tamanho de fonte menor para o parágrafo */
  max-width: 600px; /* Define uma largura máxima para o parágrafo */
  margin: 0 auto; /* Centraliza o parágrafo horizontalmente */
}
</style>