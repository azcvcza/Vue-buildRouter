<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <p>{{type}}</p>
    <p>{{weight}}</p>
    <p>{{height}}</p>
      
  </div>
</template>

<script>
export default {
  name: 'C',
  data () {
    return {
      name: 'C c c c ',
      type:'ground',
      weight:'179LB',
      height:'1.7M'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

</style>
