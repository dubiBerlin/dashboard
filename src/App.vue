<template>
  <v-app>
    <v-card width="400" class="mx-auto mt-5" >
      <v-card-title>
        <h1 class="display">Login</h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field label="Username" prepend-icon="mdi-account-circle"  />
          <v-text-field :type="showPassword?'text':'password'" label="Password" @click:append="showPassword = !showPassword"  prepend-icon="mdi-lock" :append-icon="showPassword ? 'mdi-eye':'mdi-eye-off'" >
          </v-text-field>
        </v-form>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions> 
        <v-btn color="success" >Register</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="info">Login</v-btn>
      </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    // HelloWorld,
  },

  data: () => ({
    showPassword: false
  }),
};
</script>
