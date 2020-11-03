<template>
  <v-app>
    <v-content>
      <v-row
        col="12"
        class="justify-space-around "
      >        
      <v-col
        lg="9"
        md="6"
      >
        <SaveForm />
      </v-col> 
      <v-col
        lg="2"
        md="4"
      >
        <AddressCard />
      </v-col> 
      </v-row>
    </v-content>
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
