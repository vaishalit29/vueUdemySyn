<template>
  <div>
  <div>
  
  <label class="me-2">{{ label }}</label>
  <input type="text"  @input="onInput" placeholder="Search..">
</div></div>
</template>

<script>
export default {
  name: 'SearchBox',
  props: {
    label: String
  },
  methods:{
  onInput(event){
    //  console.log(event.target.value)
    this.$emit('termChange', event.target.value )

  }
  },
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{
  width:75%;
}
div{
  text-align: center;
  margin: 20px;
}
</style>
