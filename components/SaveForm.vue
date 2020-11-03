<template>
    <v-card width="60%" class="mx-auto mt-16">
      <v-card-title>
        <h1 class="display-1"> Salve o Endereco </h1>
      </v-card-title>
      <v-card-text>
        <v-form
        >
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
          <v-text-field             
            v-model="address.logradouro"
            label="Logradouro"
          />
          <v-text-field             
            v-model="address.bairro"
            label="Bairro"
            :disabled="true"   
          />
          <v-text-field             
            v-model="address.numero"
            label="Numero"
            :rules="numberRules"
            required
          />
          <v-text-field             
            v-model="address.complemento"
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
            type="submit"
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
      saveData: [],
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
        this.validate();
      } 
    },
    async validate() {
      try{
        const res = await axios.get(
          `https://viacep.com.br/ws/${this.cep.replace(".","").replace("-","")}/json`
          );
        this.address = (res.data)
      } catch(err){
        console.log(err)
      }
    },

  },
  watch: {

  },
}
</script>
