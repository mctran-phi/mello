<template>
  <v-row align="center" justify="center">
    <v-col cols="12" sm="8" md="4" align-self="center">
      <v-card>
        <v-card-title class="justify-center">Sign up</v-card-title>
        <v-card-text>
          <v-form>
            <v-text-field
              v-model="username"
              label="Username"
              outlined
              required
              @input="$v.username.$touch()"
              @blur="$v.username.$touch()"
              :error-messages="usernameErrors"
              >
            </v-text-field>
            <v-text-field
              v-model="email"
              label="Email"
              outlined
              required
              @input="$v.email.$touch()"
              @blur="$v.email.$touch()"
              :error-messages="emailErrors"
              >
            </v-text-field>
            <v-text-field
              v-model="passowrd"
              label="Password"
              outlined
              required
              @input="$v.password.$touch()"
              @blur="$v.password.$touch()"
              :error-messages="passwordErrors"
              >
            </v-text-field>
            <v-text-field
              v-model="confirmPassword"
              label="Confirm Password"
              outlined
              required
              @input="$v.confirmPassword.$touch()"
              @blur="$v.confirmPassword.$touch()"
              :error-messages="confirmPasswordErrors"
              >
            </v-text-field>
          </v-form>
          <v-card-actions class="justify-center">
            <v-btn
              class="signin-button"
              outlined
              large
              @click="submit"
              >
              Create
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
      username: { required },
      email: { required, email },
      password: { required },
      confirmPassword: { required },
    },

    data: () => ({
      username: '',
      email: '',
      password: '',
      confirmPassword: '',
    }),

    computed: {
      usernameErrors() {
        const errors = [];
        if (!this.$v.username.$dirty) return errors;
        !this.$v.username.required && errors.push('Username is required');
        return errors;
      },
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
      confirmPasswordErrors() {
        const errors = [];
        if (!this.$v.confirmPassword.$dirty) return errors;
        !this.$v.confirmPassword.required && errors.push('Password is required');
        if (!this.$v.password !== !this.$v.confirmPassword) errors.push('Password does not match');
        return errors;
      }
    },

    methods: {
      submit() {
        this.$v.$touch();
      },
    },
  }
</script>
