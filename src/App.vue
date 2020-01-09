<template>
  <div>
    <form-helper>
      <div slot="form-header">
                <h3>This is the title of a form</h3>
                <p>This is some info about the form</p>
            </div>
            <div slot="form-fields">
                <input type="text" placeholder="name" required />
                <input type="password" placeholder="password" required />
            </div>
            <div slot="form-controls">
                <button v-on:click="handleSubmit">Submit</button>
            </div>
    </form-helper>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Content from './components/Content.vue'
import formHelper from './components/formHelper.vue'

export default {
  components:{
    'form-helper': formHelper
  },
  data () {
    return{
      title: 'Saya adalah slot title dinamik'
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
