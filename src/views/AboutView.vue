<template>
  <v-parallax dark src="/img/fundo.png" height="700">
    <v-row class="mt-12 mb-4"> <!-- Adicionando uma margem inferior menor -->
      <v-col cols="12">
        <div class="text-center">
          <h2>ABOUT ME</h2>
          <p class="smaller-paragraph">
            Here you will find more information about me, what I do, and my current skills mostly in terms of programming and technology
          </p>
        </div>
      </v-col>
    </v-row>

    <v-row class="mt-4"> <!-- Adicionando uma margem superior menor -->
        <!-- Primeira coluna -->
        <v-col cols="6" class="mb-12">
            <div class="text-center">
                <h1 class="d-lg-none text-mobile">Get to know me!</h1>
                <h1 class="d-none d-lg-block text-pc">Get to know me!</h1>
                <p>I'm a full-stack developer with experience in Angular, TypeScript, Java, Spring Boot, Vue.js, JavaScript, HTML, and CSS. I'm passionate about creating efficient and user-friendly web applications. With a strong foundation in both front-end and back-end technologies, I strive to deliver high-quality solutions that meet the needs of clients and users alike.</p>
            </div>
        </v-col>
        <!-- Segunda coluna -->
        <v-col cols="6" class="mb-12">
            <div class="text-center">
                <h1 class="d-lg-none text-mobile">My Skills!</h1>
                <h1 class="d-none d-lg-block text-pc">My Skills!</h1>
                <div class="buttons">
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-angular</v-icon> Angular </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-language-typescript</v-icon> TypeScript </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-language-java</v-icon> Java </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-power</v-icon> Spring Boot </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-vuejs</v-icon> VueJs </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-alpha-z-box-outline</v-icon> ZK Framework </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-language-html5</v-icon> HTML </v-btn>
                    <v-btn color="amber darken-1" dark class="ml-2 mt-2"><v-icon>mdi-language-css3</v-icon> CSS </v-btn>
                </div>
            </div>
        </v-col>
    </v-row>
  </v-parallax>
</template>

<style scoped>
h2 {
  color: black;
  margin-bottom: 0.5em;
  font-size: 48px;
  font-weight: 700;
  border-bottom: 6px solid #ffb300; /* Adiciona uma borda preta com 2 pixels de largura */
  display: inline-block; /* Para que a borda se ajuste ao texto */
  padding-bottom: 0.2em; /* Ajusta o espaço entre o texto e a borda */
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