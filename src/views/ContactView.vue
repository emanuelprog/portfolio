<template>
  <v-container>
    <v-row class="mt-12 mb-4">
      <v-col cols="12">
        <div class="text-center">
          <h2 class="fade-in">
            {{ language === "pt" ? "CONTATO" : "CONTACT ME" }}
          </h2>
          <div class="underline fade-in"></div>
          <p class="smaller-paragraph fade-in">
            {{
              language === "pt"
                ? "Sinta-se à vontade para entrar em contato comigo enviando o formulário abaixo e entrarei em contato com você o mais breve possível."
                : "Feel free to contact me by submitting the form below, and I will get back to you as soon as possible."
            }}
          </p>
        </div>
      </v-col>
    </v-row>

    <v-divider class="mb-12 fade-in"></v-divider>

    <v-row class="mb-4 fade-in">
      <v-col cols="12" sm="8" md="6" class="text-center">
        <div class="d-flex justify-center align-center" style="height: 100%;">
          <div style="background-color: #212121; padding: 5px; border-radius: 50%;">
            <img src="/img/world.svg" style="width: 330px; height: 330px; border-radius: 50%; object-fit: cover;">
          </div>
        </div>
        <div class="mb-5">
          <v-icon v-bind="attrs" v-on="on" size="24px" color="grey darken-4">mdi-crosshairs-gps</v-icon><span style="font-weight: bolder; margin-left: 5px">{{ language === "pt" ? "Campo Grande MS - Brasil" : "Campo Grande MS - Brazil" }}</span>
        </div>
      </v-col>
      <v-col cols="12" sm="8" md="6" class="mt-5">
        <v-card class="pa-6" elevation="6">
          <form>
            <v-text-field
              v-model="name"
              :error-messages="nameErrors"
              :counter="10"
              :label="language === 'pt' ? 'Digite seu nome' : 'Enter Your Name'"
              required
              @input="$v.name.$touch()"
              @blur="$v.name.$touch()"
            ></v-text-field>
            <v-text-field
              v-model="email"
              :error-messages="emailErrors"
              :label="
                language === 'pt' ? 'Digite seu e-mail' : 'Enter Your E-mail'
              "
              required
              @input="$v.email.$touch()"
              @blur="$v.email.$touch()"
            ></v-text-field>

            <v-text-field
              v-model="message"
              :error-messages="messageErrors"
              :label="
                language === 'pt' ? 'Digite sua mensagem' : 'Enter Your Message'
              "
              required
              @input="$v.message.$touch()"
              @blur="$v.message.$touch()"
              height="100px"
              class="mb-12"
            ></v-text-field>

            <v-row justify="center">
              <v-btn class="mr-4" @click="submit" color="amber darken-1">
                {{ language === "pt" ? "ENVIAR" : "SUBMIT" }}
              </v-btn>
              <v-btn @click="clear" color="red">
                {{ language === "pt" ? "LIMPAR" : "CLEAR" }}
              </v-btn>
            </v-row>
          </form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required, maxLength, email } from "vuelidate/lib/validators";

export default {
  props: ["language"],
  mixins: [validationMixin],

  validations: {
    name: { required, maxLength: maxLength(10) },
    email: { required, email },
    message: { required }, // Corrigido para required
  },

  data: () => ({
    name: "",
    email: "",
    message: "",
  }),

  computed: {
    nameErrors() {
      const errors = [];
      if (!this.$v.name.$dirty) return errors;
      if (!this.$v.name.maxLength) {
        errors.push(
          this.language === "pt"
            ? "O nome deve ter no máximo 10 caracteres."
            : "Name must be at most 10 characters long"
        );
      }
      if (!this.$v.name.required) {
        errors.push(
          this.language === "pt" ? "O nome é obrigatório." : "Name is required."
        );
      }
      return errors;
    },
    messageErrors() {
      const errors = [];
      if (!this.$v.message.$dirty) return errors;
      if (!this.$v.message.required) {
        errors.push(
          this.language === "pt"
            ? "A mensagem é obrigatória."
            : "Message is required."
        );
      }
      return errors;
    },
    emailErrors() {
      const errors = [];
      if (!this.$v.email.$dirty) return errors;
      if (!this.$v.email.email) {
        errors.push(
          this.language === "pt"
            ? "Deve ser um e-mail válido."
            : "Must be valid e-mail"
        );
      }
      if (!this.$v.email.required) {
        errors.push(
          this.language === "pt"
            ? "O e-mail é obrigatório."
            : "E-mail is required"
        );
      }
      return errors;
    },
  },

  methods: {
    submit() {
      this.$v.$touch();
    },
    clear() {
      this.$v.$reset();
      this.name = "";
      this.email = "";
      this.message = "";
    },
    mounted() {
      // Adiciona a classe 'active' após um pequeno atraso para acionar a animação de fade-in
      setTimeout(() => {
        document.querySelector(".fade-in-form").classList.add("active");
      }, 100);
    },
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

p {
  color: black;
}

.smaller-paragraph {
  font-size: 1.1em; /* Define um tamanho de fonte menor para o parágrafo */
  max-width: 800px; /* Define uma largura máxima para o parágrafo */
  margin: 0 auto; /* Centraliza o parágrafo horizontalmente */
}
</style>