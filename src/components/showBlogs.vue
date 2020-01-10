<template>
  <div v-theme="'narrow'" id="show-blogs">
    <h1>All Blog Articles</h1>
    <input type="text" v-model="search" placeholder="Search post"/>
    <div class="single-blog" v-for="blog in filteredBlogs">
      <router-link v-bind:to="'/blog/' + blog.id"><h2>{{blog.title | hurufBesar }}</h2></router-link>
      <article>
        {{ blog.content | snippet }}
      </article>
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
    this.$http.get('https://belajar-vue-305bd.firebaseio.com/post.json').then(function(data){
      return data.json();
    }).then(function(data){
      var blogsArray = [];
      for(let key in data){
        data[key].id = key
        blogsArray.push(data[key]);
      }
      this.blogs = blogsArray;
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
a{
    text-decoration: none;
    color: black;
}
a:hover{
    text-decoration: none;
    color: #444;
}
input{
  width:100%;
  height: 30px;
}
</style>
