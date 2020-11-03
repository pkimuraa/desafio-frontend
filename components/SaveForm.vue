<template>
    <v-card class="">
      <v-card-title>
        <h1 class="display-1"> Salve o Endereco </h1>
      </v-card-title>
      <v-card-text>
        <validation-observer
          ref="observer"
          v-slot={invalid}
        >
          <v-form
            ref="form"
            v-model="valid"
          >
            <ValidationProvider
              rules="required"
              name="CEP"
            >
              <v-row
                class="align-bottom"
              >
                <v-col
                  cols="12"
                  lg="6"
                  sm="6"
                >
                  <v-text-field
                  v-model="cep"
                  :rules ="cepRules"
                  required
                  v-mask="'##.###-###'" 
                  label="CEP" 
                  id="zipcode"
                  name="zipcode" 
                  type="numbers"
                  maxlength="10"
                  minlength="10"
                  />
                </v-col>
                <v-col
                  class="d-flex align-center justify-end"
                  lg="3"
                >
                  <v-btn 
                    @click="search"
                  >
                  Verificar CEP
                  </v-btn>
                </v-col>
              </v-row>
            </ValidationProvider>
              <v-text-field             
                v-model="address.logradouro"
                label="Logradouro"
              />
              <v-text-field             
                v-model="address.bairro"
                label="Bairro"
                :disabled="true"   
              />
            <ValidationProvider
              rules="required"
              name="numero"
            >
              <v-text-field             
                v-model="address.numero"
                label="Numero"
                :rules="numberRules"
                required
              />
            </ValidationProvider>  
              <v-text-field             
                v-model="address.complemento"
                label="Complemento"
              />
            <ValidationProvider
              rules="required"
              name="city"
            >              
              <v-text-field             
                v-model="address.localidade"
                label="Cidade"
                :disabled="true"
              />
            </ValidationProvider>
              <v-text-field             
                v-model="address.uf"
                label="Estado"
                :disabled="true"
              />
              
          </v-form> 

          <v-card-actions 
            class="d-flex justify-end"
            width="100%"
          >          
            <v-btn
              color="success"
              v-on:click.prevent ="saveAddress(address)"
              :disabled="invalid"
            > 
            Salvar 
            </v-btn>
          </v-card-actions>
        </validation-observer>
      </v-card-text>
    </v-card>
</template>

<script>
import {TheMask} from 'vue-the-mask'
import axios from 'axios'
import { extend, ValidationObserver, ValidationProvider } from "vee-validate";
import { required } from 'vee-validate/dist/rules'

extend('required',{
  ...required
})

export default {

  components: {
    TheMask,
    ValidationObserver: ValidationObserver,
    ValidationProvider: ValidationProvider

  },
  data () {
    return {
      valid: true,
      cep: "",
      address: {},
      cepRules: [
        v => !!v || 'Insira um CEP',
        v => v.length >= 10  || 'Insira um CEP Valido', 
      ],
      numberRules: [
        v => !!v || 'Favor inserir o numero da residencia'
      ]
    }

  },
  methods: {
    search(){
      if(this.cep && this.cep.length === 10){  
        this.getData();
      } else {
        this.validate ();
      }
    },
    async getData() {
      try{
        const res = await axios.get(
          `https://viacep.com.br/ws/${this.cep.replace(".","").replace("-","")}/json`
          );
        this.address = (res.data)
      } catch(err){
        const errorType = error.response.status;
        console.log(error.response)
        if(errorType === 500){
      }  
      }
    },
    saveAddress(address){
      this.$refs.observer.validate()
      var addresses = localStorage.getItem('enderecosSalvos')
      if(addresses) {
        
        addresses = JSON.parse(addresses)
        addresses.push(address)
      } else {
        addresses = [address]
      }

      localStorage.setItem('enderecosSalvos', JSON.stringify(addresses))
    },
    validate(){
      this.$refs.form.validate()
    }
  },
  watch: {
        
  }
}
</script>
