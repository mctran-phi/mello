<template>
  <v-row align="center" justify="center">
    <v-col cols="12" sm="8" md="4" align="center">
      <v-card>
        <v-card-title class="signin-title justify-center">Mello</v-card-title>
        <v-card-text>
          <v-form>
            <v-text-field
              v-model="email"
              label="Email"
              outlined
              required
              prepend-inner-icon="mdi-mail"
              @input="$v.email.$touch()"
              @blur="$v.email.$touch()"
              :error-messages="emailErrors"
              >
            </v-text-field>
            <v-text-field
              v-model="password"
              label="Password"
              type="password"
              outlined
              required
              prepend-inner-icon="mdi-lock"
              @input="$v.password.$touch()"
              @blur="$v.password.$touch()"
              :error-messages="passwordErrors"
              >
            </v-text-field>
          </v-form>
          <div class="signin-link">
            <p>Don't have an account?</p>
            <a href="signup">Register here</a>
          </div>
          <div class="signin-link">
            <p>Forgot password?</p>
          </div>
          <v-card-actions class="justify-center">
            <v-btn
              class="signin-button"
              outlined
              large
              @click="submit"
              >
              Login
            </v-btn>
          </v-card-actions>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
  import { validationMixin } from 'vuelidate'
  import { required, email } from 'vuelidate/lib/validators'

  export default {
    mixins: [validationMixin],

    validations: {
      email: { required, email },
      password: { required },
    },

    data: () => ({
      email: '',
      password: '',
    }),

    computed: {
      emailErrors() {
        const errors = [];
        if (!this.$v.email.$dirty) return errors;
        !this.$v.email.email && errors.push('Must be valid e-mail');
        !this.$v.email.required && errors.push('E-mail is required');
        return errors;
      },
      passwordErrors() {
        const errors = [];
        if (!this.$v.password.$dirty) return errors;
        !this.$v.password.required && errors.push('Password is required.');
        return errors;
      },
    },

    methods: {
      submit() {
        this.$v.$touch();
      },
    },
  }
</script>
