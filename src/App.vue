<template>
  <div>
    <keep-alive>
    <component v-bind:is="component"></component>
    </keep-alive>
    <button @click="component = 'form-one'">Show form one</button>
    <button @click="component = 'form-two'">Show form Two</button>
  </div>
</template>

<script>
import formOne from './components/formOne.vue'
import formTwo from './components/formTwo.vue'

export default {
  components:{
    'form-one': formOne,
    'form-two': formTwo
  },
  data () {
    return{
      component:'form-two'
    }
  },
  methods: {
    handleSubmit: function(){
      alert('Thanks For Submitting')
    }
  }
}
</script>

<style>
body{
    margin: 0;
    font-family: 'Nunito SemiBold';
}
</style>
