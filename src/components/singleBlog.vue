<template>
  <div id="single-blog">
    <router-link to="/">
      <button type="button" name="button">Back</button>
    </router-link>
    <h1>{{ blog.title }}</h1>
    <p>Author : {{ blog.author }}</p>
    <article>
      {{ blog.content }}
    </article>
    <ul>
      <li v-for="category in blog.checkcategories">{{ category }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return{
      id: this.$route.params.id,
      blog: {}
    }
  },
  created() {
    this.$http.get('https://belajar-vue-305bd.firebaseio.com/post/' + this.id + '.json').then(function(data){
      return data.json();
    }).then(function(data){
      this.blog = data;
    })
  }
}
</script>

<style scoped>
#single-blog{
  max-width: 960px;
  margin: 0 auto;
}
</style>
