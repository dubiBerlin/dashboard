<template>
<v-container>
  <v-row>
  <v-col >
    <h1>Signup</h1>
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
    >

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

      <v-autocomplete
        v-model="selectBrowser"
        :items="items"
        :rules="[v => !!v || 'Item is required']"
        label="Select using Browser"
        required
      ></v-autocomplete>

      <v-file-input multiple label="Profile Picture"></v-file-input>

       <v-checkbox
        v-model="agreed"
        label="Agree on Terms"
        color="red"
        value="red"
        hide-details
      ></v-checkbox>
      <v-btn
        color="success"
        class="mr-4"
        @click="validate"
      >
        Validate
      </v-btn>
    </v-form>
    </v-col>
  </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Signup",
  data(){
    return{
      email:"",
      selectBrowser:"",
      items:["Chrome","FireFox","Opera"],
      agreed:false,

    }
  },
  methods:{
    validate(){

    }
  }
}
</script>

<style scoped>

</style>