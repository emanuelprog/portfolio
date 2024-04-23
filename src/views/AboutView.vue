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
      <!-- Adicionando uma margem superior menor -->
      <!-- Primeira coluna -->
      <v-col cols="6" class="mb-12">
        <div class="text-center">
          <h1 :class="{ 'text-mobile': $vuetify.breakpoint.smAndDown, 'text-pc': !$vuetify.breakpoint.smAndDown }">{{ language === 'pt' ? 'Me conheça!' : 'Get to know me!' }}</h1>
          <p>
            {{ language === 'pt' ? 'Sou um desenvolvedor full-stack com experiência em Angular, TypeScript, Java, Spring Boot, Vue.js, JavaScript, HTML e CSS. Sou apaixonado por criar aplicações web eficientes e fáceis de usar. Com uma base sólida em tecnologias front-end e back-end, me esforço para fornecer soluções de alta qualidade que atendam às necessidades de clientes e usuários.' : "I'm a full-stack developer with experience in Angular, TypeScript, Java, Spring Boot, Vue.js, JavaScript, HTML, and CSS. I'm passionate about creating efficient and user-friendly web applications. With a strong foundation in both front-end and back-end technologies, I strive to deliver high-quality solutions that meet the needs of clients and users alike." }}
          </p>
        </div>
      </v-col>
      <!-- Segunda coluna -->
      <v-col cols="6" class="mb-12">
        <div class="text-center">
          <h1 :class="{ 'text-mobile': $vuetify.breakpoint.smAndDown, 'text-pc': !$vuetify.breakpoint.smAndDown }">{{ language === 'pt' ? 'Meus Conhecimentos!' : 'My Skills!' }}</h1>
          <div class="buttons">
            <v-btn color="amber darken-1" dark class="ml-2 mt-2"
              ><v-icon>mdi-angular</v-icon> Angular
            </v-btn>
            <!-- Adicione os outros botões aqui -->
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