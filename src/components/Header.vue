<template>
  <nav>
    <ul>
      <li><router-link to="/">Blog</router-link></li>
      <li><router-link to="/add">Add Post</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {

}
</script>

<style scoped>

ul{
    list-style-type: none;
    text-align: center;
    margin: 0;
}
li{
    display: inline-block;
    margin: 0 10px;
}
a{
    color: #fff;
    text-decoration: none;
    padding: 6px 8px;
    border-radius: 5px;
}
nav{
    background: #222;
    padding: 14px;
    margin-bottom: 40px;
}
.router-link-exact-active{
    background: #eee;
    color: #444;
}
</style>
