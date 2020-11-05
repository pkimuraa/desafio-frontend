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
        <AddressCard />
      </v-col> 
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import SaveForm from "../components/SaveForm"
import AddressCard from "../components/AddressCard"

export default {
  components: {
    SaveForm,
    AddressCard
  },
  data () {
    return {
    }
  }
}
</script>
