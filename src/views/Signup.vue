<template>
<v-container >
  <v-row  style="width:70%; margin: 0 auto; padding: 10px;">
  <v-col>
    <h1>Signup</h1>
    <v-form
      ref="signUpForm"
      v-model="formValided"
    >

      <v-text-field
        v-model="email"
        label="E-mail"
        required
        :rules="emailRules"
      ></v-text-field>

      <v-autocomplete
        v-model="selectBrowser"
        :items="items"
        label="Select using Browser"
      ></v-autocomplete>
      <v-file-input multiple label="Profile Picture"></v-file-input>
      <v-text-field 
        label="Birthday" 
        v-model="birthday"  
        readonly 
      ></v-text-field>
      <v-date-picker
        v-model="birthday"
      ></v-date-picker>
       <v-checkbox
        v-model="agreed"
        label="Agree on Terms & Conditions"
        color="red"
        :rules="agreeToTermsRules"
        required
      ></v-checkbox>
      <v-btn
        type="submit"
        color="primary"
        class="mr-4" 
        :disabled="!formValided"
      >
        Submit
      </v-btn>
      <v-btn class="mr-4" color="success" @click="validateForm" >Validate Form</v-btn>
      <v-btn class="mr-4" color="warning" @click="resetValidation" >Reset Validation</v-btn>
      <v-btn color="error" @click="resetForm" >Reset</v-btn>
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
      agreeToTermsRules:[value=>!!value || "You must agree to the terms and conditions to sign up for an account!" ],
      email:"",
      selectBrowser:"",
      items:["Chrome","FireFox","Opera", "Edge","Brave"],
      agreed:false,
      birthday:"",
      formValided:false,
      emailRules:[
        value => !!value || "Email is required",
        value => value.indexOf("@")!==0 || "Email should have a username.",
        value => value.includes("@") || "Email should include an @ symbol.",
        value => value.includes('.') || 'Email should include a period symbol.',
        value => value.indexOf(".") - value.indexOf("@") > 1 || "Email should contain a valid domain.",
        value => value.indexOf(".") <= value.length - 3 || "Email should contain a valid domain extension."
         ]
    }
  },
  methods:{
    resetForm(){
      this.$refs.signUpForm.reset();
    },
    resetValidation(){
      this.$refs.signUpForm.resetValidation();
    },
    validateForm(){
      this.$refs.signUpForm.validate();
    }
  }
}
</script>

<style scoped>

</style>