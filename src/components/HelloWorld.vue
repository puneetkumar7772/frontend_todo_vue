<template>
  <div class="hello">
    <Card :CardHeading = "CardHeading"/>
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'HelloWorld',
  components:{
    Card
  },
  props: {
    msg: String,
    CardHeading:String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
