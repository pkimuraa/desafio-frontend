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
          value=""
          />
          <v-row
            class="align-bottom"
          >
            <v-col
              cols="12"
              lg="9"
              sm="8"
            >
              <v-text-field
              class=""
              v-model="cep"
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
          <v-text-field             
            v-model="address.logradouro"
            label="Logradouro"
            :disabled="true"
          />
          <v-text-field             
            v-model="address.bairro"
            label="Bairro"
            :disabled="true"
          />
          <v-text-field             
            v-model="number"
            label="Numero"
            required="true"
          />
          <v-text-field             
            v-model="complement"
            label="Complemento"
          />
          <v-text-field             
            v-model="address.localidade"
            label="Cidade"
            :disabled="true"
          />
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
          > 
          Salvar 
          </v-btn>
        </v-card-actions>
      </v-card-text>
    </v-card>
</template>

<script>
import {TheMask} from 'vue-the-mask'
import axios from 'axios'
 
export default {
  components: {
    TheMask
  },
  data () {
    return {
      cep: "",
      address: {},
      number: "",
      complement: ""
    }

  },
  methods: {
    search(){
      if(this.cep && this.cep.length === 10){
        this.validate();
      }
    },
    async validate() {
      try{
        const res = await axios.get(
          `https://viacep.com.br/ws/${this.cep.replace(".","").replace("-","")}/json`
          );
          this.address = (res.data)
        console.log(res.data) 
      } catch(err){

        console.log(err)
      }
    }, 
  },
  watch: {

  },

}
</script>
