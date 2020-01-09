<template>
  <header>
    <h1 v-on:click="changeTitle">{{title}}</h1>
  </header>
</template>

<script>
import { bus } from '../main';

export default {
  props: {
    title: {
      type: String
    }
  },
  data () {
    return{

    }
  },
  methods: {
    changeTitle: function(){
      // this.$emit('ubahJudul', 'Vue App');
      this.title = 'Vue App';
      bus.$emit('ubahJudul', 'Vue App');
    }
  }
}
</script>

<style scoped>
header{
  background: lightgreen;
  padding: 10px;
}
h1{
  text-align: center;
  color: #222;
}

</style>
