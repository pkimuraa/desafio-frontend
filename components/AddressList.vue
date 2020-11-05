<template>
  <v-card >
    <v-card-title
      class="pb-3"
    > 
      Meus Enderecos 
    </v-card-title>
    <v-container

      v-for="address in addresses"
    >
      <v-row
        class="justify-space-between align-item-center"
      >
        <v-card-subtitle
          class="font-weight-bold pa-3"          
        > 
          Endereco
        </v-card-subtitle>
        <v-card-actions>
          <v-btn
            icon
            color="error"
            depressed
            @click="deleteOverlay = !deleteOverlay"
          >
          <v-icon>mdi-trash-can</v-icon>
          </v-btn>
          <v-overlay
            :value="deleteOverlay"
          >
            <v-sheet
              width="450"
              elevation="2"
              height="150"
            >
              <v-row
                class="justify-center align-item-center"
              >
                <v-col
                  sm="12"
                >
                <p class="text-center pt-3">Voce tem certeza que quer deletar o endereco?</p>
                </v-col>
                <v-col
                  sm="8"
                  class="d-flex justify-space-around pa-0"
                >
                <v-btn
                  color="secondary"
                  @click="deleteOverlay=false"
                > Cancelar </v-btn>
                <v-btn
                  color="error"
                  @click.prevent="removeAddress(address.id)"
                > 
                  Deletar
                </v-btn>
                </v-col>
              </v-row>
            </v-sheet>
          </v-overlay>

          <v-btn
            icon
            depressed
            color="secondary"
          > 
          <v-icon>mdi-clipboard-edit</v-icon>
          </v-btn>
        </v-card-actions>
      </v-row>
      <v-row
        class="justify-center"
      >
        <v-col
          sm="12"
        >
          <v-card-text
            class="pa-0 "
          > 
            Logradouro: {{address.logradouro}}
          </v-card-text>
        </v-col>
        <v-col
          sm="6"
        >
          <v-card-text 
            class="pa-0"            
          > 
            CEP: {{address.cep}} 
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Bairro: {{address.bairro}}
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Numero: {{address.numero}}
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Complemento: {{address.complemento}}
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Cidade:  {{address.localidade}}
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            UF: {{address.uf}}
          </v-card-text>
        </v-col>

      </v-row>
    <v-divider />
    </v-container>
   
  </v-card>
</template>

<script>

 
export default {
  components: {
  },
  data () {
    return{
      deleteOverlay: false,
      addresses: []
    }
  },
  created(){
    },
  mounted(){
    this.addresses = JSON.parse(localStorage.getItem('enderecosSalvos'))

  },
  methods:{
    removeAddress(addressId){
      let addresses = localStorage.getItem('enderecosSalvos')
      if(!addresses) return;
      addresses = JSON.parse(addresses)
      addresses = addresses.filter((address) => {
        return address.id != addressId
      });

      this.addresses = addresses;

      localStorage.setItem('enderecosSalvos', JSON.stringify(addresses))
      deleteOverlay=false
    }
  },
  watch:{
  }

}
</script>
