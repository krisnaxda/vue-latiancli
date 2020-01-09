<template>
  <div v-theme="'narrow'" id="show-blogs">
    <h1>All Blog List</h1>
    <input type="text" v-model="search" placeholder="Search post"/>
    <div class="single-blog" v-for="blog in filteredBlogs">
      <h2>{{blog.title | hurufBesar }}</h2>
    </div>
  </div>
</template>

<script>
import searchMixin from '../mixins/searchMixin';
export default {
  data(){
    return{
      blogs: [],
      search: ''
    }
  },
  methods: {

  },
  created() {
    this.$http.get('https://jsonplaceholder.typicode.com/posts').then(function(data){
      this.blogs = data.body.slice(0,10);
    })
  },
  computed: {

  },
  filters: {
    // tidak memakai function
    // hurufBesar(data){
    //Memakai Function
    'hurufBesar': function(data){
      return data.toUpperCase()
    },
  },
  directives: {
    'warnawarni':{
      bind(el,binding,vnode){
        el.style.color = "#" + Math.random().toString().slice(2,8)
      }
    }
  },
  mixins: [searchMixin]
}
</script>

<style scoped>
#show-blogs{
    max-width: 800px;
    margin: 0px auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
h2{
  font-family: montserrat;
}
input{
  width:100%;
  height: 30px;
}
</style>
