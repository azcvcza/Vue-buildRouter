<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <div class="container">
      <div class="item">|Type|<h3>{{type}}</h3></div>
      <div class="item">|Weight|<h3>{{weight}}</h3></div>
      <div class="item">|Height|<h3>{{height}}</h3></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'A',
  data () {
    return {
      name: 'A a a a ',
      type:'fire',
      weight:'199LB',
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
.hello{
  display: flex;
  flex-direction: column;
  justify-content: center
}
.container{
  display:flex;
  flex-direction: row;
  justify-content: center
}

</style>
