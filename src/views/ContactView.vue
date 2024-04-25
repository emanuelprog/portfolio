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
        <div
          class="d-flex justify-center align-center mt-3"
          style="height: 100%"
        >
          <div style="width: 100%">
            <iframe
              v-if="language === 'pt'"
              style="
                border-radius: 5px;
                box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
              "
              width="400"
              height="400"
              frameborder="0"
              scrolling="no"
              marginheight="0"
              marginwidth="0"
              src="https://maps.google.com/maps?width=386&amp;height=386&amp;q=Campo%20Grande+(My%20Business%20Name)&amp;t=&amp;z=2&amp;ie=UTF8&amp;iwloc=B&amp;output=embed&amp;hl=pt"
              ><a href="https://www.gps.ie/">gps trackers</a></iframe>
            <iframe
              v-else
              style="
                border-radius: 5px;
                box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
              "
              width="400"
              height="400"
              frameborder="0"
              scrolling="no"
              marginheight="0"
              marginwidth="0"
              src="https://maps.google.com/maps?width=386&amp;height=386&amp;q=Campo%20Grande+(My%20Business%20Name)&amp;t=&amp;z=2&amp;ie=UTF8&amp;iwloc=B&amp;output=embed&amp;hl=en"
              ><a href="https://www.gps.ie/">gps trackers</a></iframe>
          </div>
        </div>
      </v-col>
      <v-col cols="12" sm="8" md="6" class="mt-5">
        <v-card class="pa-6" elevation="6">
          <form>
            <v-text-field
              v-model="name"
              :error-messages="nameErrors"
              :counter="30"
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
              <v-btn
                class="mr-4"
                @click="submit"
                :disabled="dialog"
                :loading="dialog"
                color="grey darken-4"
                style="color: white"
              >
                {{ language === "pt" ? "ENVIAR" : "SUBMIT" }}
              </v-btn>
              <v-dialog v-model="dialog" hide-overlay persistent width="300">
                <v-card color="amber darken-1" dark>
                  <v-card-text v-if="sucess === false">
                    {{ language === "pt" ? "Enviando..." : "Sending..." }}
                    <v-progress-linear
                      indeterminate
                      color="white"
                      class="mb-0"
                    ></v-progress-linear>
                  </v-card-text>

                  <v-card-text v-else>
                    {{
                      language === "pt"
                        ? "Email enviado com sucesso!"
                        : "Email sent successfully!"
                    }}
                    <v-icon color="green darken-2" class="ml-2 mr-2"
                      >mdi-check-circle</v-icon
                    >
                  </v-card-text>
                </v-card>
              </v-dialog>
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
import { eventBus } from "@/event-bus.js";

export default {
  props: ["language"],
  mixins: [validationMixin],
  validations: {
    name: { required, maxLength: maxLength(30) },
    email: { required, email },
    message: { required },
  },

  data: () => ({
    name: "",
    email: "",
    message: "",
    dialog: false,
    sucess: false
  }),
  watch: {
    dialog(val) {
      if (!val) return;

      setTimeout(() => (this.dialog = false), 4000);
    },
  },

  computed: {
    nameErrors() {
      const errors = [];
      if (!this.$v.name.$dirty) return errors;
      if (!this.$v.name.maxLength) {
        errors.push(
          this.language === "pt"
            ? "O nome deve ter no máximo 30 caracteres."
            : "Name must be at most 30 characters long"
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

      this.dialog = true;

      this.sucess = false;

      if (this.email == "") {
        this.dialog = false;
        return;
      }
      if (this.name == "") {
        this.dialog = false;
        return;
      }

      if (this.message == "") {
        this.dialog = false;
        return;
      }
      (function () {
        emailjs.init("3uYAFRE_bkzXqlraO");
      })();

      var params = {
        subject: this.name,
        to: "emanuelhamachi@hotmail.com",
        replyto: this.email,
        message: this.message,
      };

      var serviceID = "service_bdnsp4r";

      var templateID = "template_vr7bd89";

      emailjs
        .send(serviceID, templateID, params)
        .then((res) => {
          this.sucess = true;
          setTimeout(() => {
            this.dialog = false;
            this.clear();
          }, 2000);
        })
        .catch();
    },
    clear() {
      this.$v.$reset();
      this.name = "";
      this.email = "";
      this.message = "";
      this.sucess = false;
      this.dialog = false;
    },
    mounted() {
      setTimeout(() => {
        document.querySelector(".fade-in-form").classList.add("active");
      }, 100);
    },
  },
};
</script>

<style scoped>
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

p {
  color: black;
}

.smaller-paragraph {
  font-size: 1.1em;
  max-width: 800px;
  margin: 0 auto;
}

.divider {
  width: 100%;
  height: 1px;
  background-color: rgba(0, 0, 0, 0.12);
  margin-top: 20px;
}
</style>