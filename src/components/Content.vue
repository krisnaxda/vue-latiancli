<template>
  <div id="menu">
    <ul>
      <li v-for="menus in menu" @click="menus.show = !menus.show">
        <h2>{{menus.name}}</h2>
        <h3 v-show="menus.show">{{menus.Price}}</h3>
      </li>
    </ul>
    <button v-on:click="deleteMenu">Delete Menu</button>
  </div>
</template>

<script>
export default {
  // props: ['menu'] ->INI PROPS LANGSUNG
  //Kode di bawah adalah Props VALIDATION
  props: {
    menu: {
      type: Array,
      required: true
    }
  },
  data () {
    return{

    }
  },
  methods:{
    deleteMenu: function(){
      this.menu.pop();
    }
  },

  //Lifecycle Hooks
  // beforeCreate(){
  //   alert('beforeCreate');
  // },
  // created(){
  //   alert('Created');
  // },
  // beforeMount(){
  //   alert('beforeMount');
  // },
  // mounted(){
  //   alert('mounted');
  // },
  // beforeUpdate(){
  //   alert('beforeUpdate');
  // },
  // updated(){
  //   alert('updated');
  // },

}
</script>

<style scoped>
#menu{
    width: 100%;
    max-width: 1200px;
    margin: 40px auto;
    padding: 0 20px;
    box-sizing: border-box;
}
ul{
    display: flex;
    flex-wrap: wrap;
    list-style-type: none;
    padding: 0;
}
li{
    flex-grow: 1;
    flex-basis: 300px;
    text-align: center;
    padding: 30px;
    border: 1px solid #222;
    margin: 10px;
}
</style>
