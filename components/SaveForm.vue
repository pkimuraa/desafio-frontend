<template>
    <v-card width="60%" class="mx-auto mt-16">
      <v-card-title>
        <h1 class="display-1"> Salve o Endereco </h1>
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field 
          label="Nome do endereco" 
          name="adress-name" 
          />
          <v-text-field 
          v-mask="'##.###-###'"
          label="CEP" 
          id="zipcode"
          name="zipcode" 
          type="numbers"
          maxlength="10"
          minlength="10"
          />
        </v-form> 
        <v-card-actions>
          <v-btn 
          v-on:click="validate"
          color="success">
           Prosseguir </v-btn>
          <v-btn class="d-none" > Salvar </v-btn>
        </v-card-actions>

      </v-card-text>
    </v-card>
</template>

<script>
import {TheMask} from 'vue-the-mask'
import axios from 'axios'



export default {
  methods: {
    async validate({ $axios }) {
      var inputVal = document.getElementById("zipcode")
      try{
        console.log(inputVal.value)
        //const res = await axios.get('https://viacep.com.br/ws/'+ inputVal.value +'/json/');
        //console.log(res.data)
      } catch(err){
        console.log(err)
      }
    },
  },
  data () {
    return {
      components: {TheMask},
      adress: []
  }



    //const res = await axios.get('https://viacep.com.br/ws');
  }
}
</script>
