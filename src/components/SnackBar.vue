<template>
  <v-snackbar
    v-model="show"
  >
    {{ text }}

    <template v-slot:action="{ attrs }">
      <v-btn
        color="blue"
        text
        v-bind="attrs"
        @click="closeSnackbar()"
      >
        Close
      </v-btn>
    </template>
  </v-snackbar>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false
    },
    text: {
      type: String,
      default: ""
    }
  },

  watch: {
    show(newValue){
      if(newValue){
        setTimeout(()=>{
          this.closeSnackbar()
        },3000);
      }
    }
  },

  methods: {
    closeSnackbar(){
      this.$emit('closeSnackbar')
    }
  }
}
</script>

<style>

</style>