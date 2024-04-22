<template>
  <v-parallax
    dark
    src="/img/fundo.png"
    :height="isMobile ? 1000 : 600"
  >
    <v-container fluid>
      <v-row class="mt-6 mb-12"> <!-- Adicione um espaço superior de 6 unidades -->
        <v-col
          v-for="(card, index) in cards"
          :key="index"
          :cols="$vuetify.breakpoint.smAndDown ? 12 : card.flex"
        >
          <v-card class="transparent-card mb-12">
            <v-carousel height="300" hide-delimiters>
              <v-carousel-item
                v-for="(item, i) in card.images"
                :key="i"
                :src="item.src"
                reverse-transition="fade-transition"
                transition="fade-transition"
              >
                <v-img :src="item.src" max-height="600"></v-img>
              </v-carousel-item>
            </v-carousel>

            <v-card-actions>
              <span style="font-weight: bolder">{{ card.title }}</span>
              <v-spacer></v-spacer>
              <v-btn icon>
                <v-icon>mdi-heart</v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-parallax>
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
.transparent-card {
  background-color: transparent !important;
}
.mt-6 {
  margin-top: 6rem !important;
}
</style>