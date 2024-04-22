<template>
  <v-parallax dark src="/img/fundo.png" height="700">
    <v-row class="mt-12">
      <v-col cols="12">
        <div class="text-center">
          <h2>HEY, I'M EMANUEL BESSA</h2>
          <p class="smaller-paragraph">
            A full-stack developer fluent in Java/Spring (backend) and
            Angular/Vue (frontend). I specialize in crafting seamless digital
            experiences. Let's collaborate and elevate your next project!
          </p>

          <div class="text-center mt-5">
            <router-link to="/projects">
              <v-btn x-large color="amber darken-1" dark> PROJECTS </v-btn>
            </router-link>
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