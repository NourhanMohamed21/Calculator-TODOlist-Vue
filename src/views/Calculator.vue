<template>
  <div class="home">
  
<Calculator/>

  </div>
</template>

<script>
// @ is an alias to /src
 import Calculator from '@/components/calculator.vue'

export default {
  name: 'Home',
  components: {
    Calculator
 
  }
}
</script>
