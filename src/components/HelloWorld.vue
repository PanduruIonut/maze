<template>
  <div class="hello">
   <InputForm/>
  </div>
</template>

<script>
import InputForm from '@/components/InputForm'

export default {
  name: 'HelloWorld',

    components: {
      InputForm,
  },
  props: {
    msg: String
  },
setup() {
  
 return {
      InputForm,
    }
}
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
