<template>
  <div>
    <!-- <add-blog></add-blog> -->
    <router-view></router-view>
  </div>
</template>

<script>
import addBlog from './components/addBlog.vue';
import showBlogs from './components/showBlogs.vue';
import listBlogs from './components/listBlogs.vue';

export default {
  components:{
    'add-blog' : addBlog,
    'show-blog' : showBlogs,
    'list-blog' : listBlogs
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
