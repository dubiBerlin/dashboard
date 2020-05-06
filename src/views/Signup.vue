<template>
  <div  style="width:550px; margin:0 auto">
  <v-card >
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

      <v-select
        v-model="selectBrowser"
        :items="items"
        :rules="[v => !!v || 'Item is required']"
        label="Browser"
        required
      ></v-select>

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
  </v-card></div>
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