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
        <SaveForm />
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
    }
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
    }
  }
}
</script>
