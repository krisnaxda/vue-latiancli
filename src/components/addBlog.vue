<template>
  <div id="add-blog">
    <h2>Add a New Blog Post</h2>
    <hr>
    <form v-if="!submitted">
      <label>Blog Title:</label>
      <input type="text" v-model.lazy="blog.title" required>
      <label>Blog Content:</label>
      <textarea v-model.lazy="blog.content"></textarea>

      <div id="checkboxes">
        <template v-for="category in categories">
          <label>{{category}}</label>
          <input type="checkbox" v-bind:value="category" v-model="blog.checkcategories">
        </template>
      </div>
      <select v-model="blog.author">
        <option v-for="author in authors">{{ author }}</option>
      </select>
      <button @click.prevent="post">Post</button>
    </form>

    <div v-if="submitted">
      <h3>Thanks for adding your post</h3>
    </div>
    <div id="preview">
      <h3>Preview Blog</h3>
      <p>
        Blog Title: {{ blog.title }}
      </p>
      <p>Blog Content:</p>
      <p> {{ blog.content }}</p>
      <p>Blog Categories : </p>
      <ul>
        <li v-for="category in blog.checkcategories">{{ category }}</li>
      </ul>
      <p>Author : {{ blog.author}}</p>
    </div>
  </div>
</template>

<script>


export default {
  components:{

  },
  data () {
    return{
      blog: {
        title: '',
        content: '',
        checkcategories: []
      },
      authors: [
        'Krisna',
        'Jarvis',
        'Friday'
      ],
      categories: [
        'sport',
        'fashion',
        'techno',
        'lifestyle'
      ],
      submitted: false
    }
  },
  methods: {
    post: function(){
      this.$http.post('https://belajar-vue-305bd.firebaseio.com/post.json', this.blog).then(function(data){
        console.log(data);
        this.submitted = true;
      });
    }
    }
  }
</script>

<style>
#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}

#checkboxes input{
  display: inline-block;
  margin-right: 10px;
}
#checkboxes label{
  display: inline-block;
}
</style>
