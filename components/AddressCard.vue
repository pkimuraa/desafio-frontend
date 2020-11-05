<template>
  <v-card >
    <v-card-title
      class="pb-0"
    > 
      Meus Enderecos 
    </v-card-title>
    <v-container>
      <v-row
        class="justify-space-between"
      >
        <v-card-subtitle
          class="font-weight-bold pa-2"          
        > 
          Endereco 1 
        </v-card-subtitle>
        <v-card-actions>
          <v-btn
            icon
            color="error"
            depressed
          > 
          <v-icon>mdi-trash-can</v-icon>
          </v-btn>
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
            Logradouro: SEPS 712/912
          </v-card-text>
        </v-col>
        <v-col
          sm="6"
        >
          <v-card-text 
            class="pa-0"            
          > 
            CEP: 70.390-125 
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Bairro: Asa Sul
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Numero: B108
          </v-card-text>
        </v-col>
        <v-col
          md="6"
        >
          <v-card-text
            class="pa-0"
          > 
            Cidade: Brasilia 
          </v-card-text>
        </v-col>
        <v-col
          md="12"
        >
          <v-card-text
            class="pa-0"
          > 
            UF: DF
          </v-card-text>
        </v-col>

      </v-row>
    </v-container>
    <v-divider />
   
  </v-card>
</template>

<script>

 
export default {
   data () {

  }
}
</script>
