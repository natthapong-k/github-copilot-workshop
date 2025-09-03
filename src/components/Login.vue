

<template>
  <v-container class="d-flex justify-center align-center" style="height: 100vh;">
    <v-dialog v-model="showDialog" persistent max-width="400">
      <template #activator="{ props }">
        <v-btn v-bind="props" color="primary" @click="showDialog = true">Login</v-btn>
      </template>
      <v-card>
        <v-card-title class="text-center">Login</v-card-title>
        <v-card-text>
          <v-form @submit.prevent="handleLogin">
            <v-text-field
              v-model="username"
              label="Username"
              required
              prepend-icon="mdi-account"
              density="compact"
            ></v-text-field>
            <v-text-field
              v-model="password"
              label="Password"
              type="password"
              required
              prepend-icon="mdi-lock"
              density="compact"
            ></v-text-field>
            <v-btn type="submit" color="primary" block class="mt-2">Login</v-btn>
          </v-form>
          <v-alert v-if="error" type="error" class="mt-4">{{ error }}</v-alert>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-container>
</template>


<script setup>
import { ref } from 'vue';

const showDialog = ref(true);
const username = ref('');
const password = ref('');
const error = ref('');

function handleLogin() {
  if (username.value === 'admin' && password.value === 'password') {
    error.value = '';
    showDialog.value = false;
    // Add navigation or state change here
  } else {
    error.value = 'Invalid username or password.';
  }
}
</script>


<!-- Vuetify handles styling, no custom CSS needed -->
