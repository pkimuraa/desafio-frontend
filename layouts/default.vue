<template>
  <v-app>
    <v-main
      class="mt-10 mr-10 ml-10"
    >
      <v-row
        col="12"
        class="justify-space-around "
      >        
      <v-col
        md="6"
      >
        <SaveForm :editingAddress="editingAddress" />
      </v-col> 
      <v-col
        md="6"
      >
        <AddressList />
      </v-col> 
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import SaveForm from "../components/SaveForm"
import AddressList from "../components/AddressList"

export default {
  components: {
    SaveForm,
    AddressList
  },
  data () {
    return {
      form: 0,
      addresses: [{
        id: "",
        cep: "",
        logradouro: "",
        localidade: "",
        uf: "",
        bairro: "",
        numero: "",
        complemento: "",
      }],
      editingAddress: null
    }
  },
  methods: {  

  }
}
</script>
