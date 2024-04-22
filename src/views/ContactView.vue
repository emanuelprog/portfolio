<template>
  <v-parallax dark src="/img/fundo.png" height="700">
    <v-row class="mt-12 mb-4">
      <v-col cols="12">
        <div class="text-center">
          <h2>CONTACT ME</h2>
          <p class="smaller-paragraph">
            Feel free to contact me by submitting the form below, and I will get back to you as soon as possible.
          </p>
        </div>
      </v-col>
    </v-row>

    <v-row justify="center" class="mb-12">
      <v-col cols="12" sm="8" md="6">
        <v-card class="pa-6">
          <form>
            <v-text-field
              v-model="name"
              :error-messages="nameErrors"
              :counter="10"
              label="Enter Your Name"
              required
              @input="$v.name.$touch()"
              @blur="$v.name.$touch()"
            ></v-text-field>
            <v-text-field
              v-model="email"
              :error-messages="emailErrors"
              label="Enter Your E-mail"
              required
              @input="$v.email.$touch()"
              @blur="$v.email.$touch()"
            ></v-text-field>

            <v-text-field
              v-model="message"
              :error-messages="messageErrors"
              label="Enter Your Message"
              required
              @input="$v.message.$touch()"
              @blur="$v.message.$touch()"
              height="100px"
              class="mb-12"
            ></v-text-field>

            <v-row justify="center">
              <v-btn
                class="mr-4"
                @click="submit"
                color="amber darken-1"
              >
                Submit
              </v-btn>
              <v-btn @click="clear" color="red">
                Clear
              </v-btn>
            </v-row>
          </form>
        </v-card>
      </v-col>
    </v-row>
  </v-parallax>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, maxLength, email } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],

  validations: {
    name: { required, maxLength: maxLength(10) },
    email: { required, email },
    message: { required } // Corrigido para required
  },

  data: () => ({
    name: '',
    email: '',
    message: ''
  }),

  computed: {
    nameErrors () {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength && errors.push('Name must be at most 10 characters long')
      !this.$v.name.required && errors.push('Name is required.')
      return errors
    },
    messageErrors () {
      const errors = []
      if (!this.$v.message.$dirty) return errors
      !this.$v.message.required && errors.push('Message is required.')
      return errors
    },
    emailErrors () {
      const errors = []
      if (!this.$v.email.$dirty) return errors
      !this.$v.email.email && errors.push('Must be valid e-mail')
      !this.$v.email.required && errors.push('E-mail is required')
      return errors
    },
  },

  methods: {
    submit () {
      this.$v.$touch()
    },
    clear () {
      this.$v.$reset()
      this.name = ''
      this.email = ''
      this.message = ''
    },
  },
}
</script>

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

p {
  color: black;
}

.smaller-paragraph {
  font-size: 1.1em; /* Define um tamanho de fonte menor para o parágrafo */
  max-width: 800px; /* Define uma largura máxima para o parágrafo */
  margin: 0 auto; /* Centraliza o parágrafo horizontalmente */
}
</style>