<template>
<v-container >
  <v-row  style="width:50%; margin: 0 auto; padding: 10px;">
  <v-col>
    <h1>Signup</h1>
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
    >

      <v-text-field
        v-model="email"
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
      <v-text-field label="Birthday" v-model="birthday"  readonly ></v-text-field>
      <v-date-picker
        v-model="birthday"
      ></v-date-picker>
       <v-checkbox
        v-model="agreed"
        label="Agree on Terms & Conditions"
        color="red"
        value="red"
        hide-details
      ></v-checkbox>
      <v-btn
        type="submit"
        color="primary"
      >
        Submit
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
      birthday:"",
      valid:""
    }
  },
  methods:{
    validate(){

    },
    emailRules(){

    }
  }
}
</script>

<style scoped>

</style>