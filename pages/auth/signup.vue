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
              >
            </v-text-field>
            <v-text-field
              v-model="email"
              label="Email"
              outlined
              required
              >
            </v-text-field>
            <v-text-field
              v-model="passowrd"
              label="Password"
              outlined
              required
              >
            </v-text-field>
            <v-text-field
              v-model="confirmPassword"
              label="Confirm Password"
              outlined
              required
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

