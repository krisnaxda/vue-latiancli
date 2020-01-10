<template>
  <div>
    <app-header></app-header>
    <router-view></router-view>
  </div>
</template>

<script>
import addBlog from './components/addBlog.vue';
import showBlogs from './components/showBlogs.vue';
import listBlogs from './components/listBlogs.vue';
import Header from './components/Header.vue';

export default {
  components:{
    'add-blog' : addBlog,
    'show-blog' : showBlogs,
    'list-blog' : listBlogs,
    'app-header' : Header
  },
  data () {
    return{

    }
  },
  methods: {

    }
  }
</script>

<style>

</style>
