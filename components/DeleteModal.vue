<template>
  <v-overlay
    :value="deleteOverlay"
  >
  </v-overlay>

</template>

<script>

 
export default {
  data () {
    return{
      deleteOverlay: false,
    }
  },
  methods:{
  },
  watch:{
    deleteOverlay(val){
      val && setTimeout(() =>{
        this.deleteOverlay = false
      }, 2000)
    },
  },
}
</script>
