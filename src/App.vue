<template>
  <div id="app">
    <PostForm/>
    <hr>
    <button @click=fetchPosts(5)>5</button>
    <button @click=fetchPosts(10)>10</button>
    <button @click=fetchPosts(20)>20</button>
    <h1>{{ postsCount }}</h1>
    <hr>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import {mapGetters, mapActions} from 'vuex'
export default {
  name: 'App',
  components: {PostForm},
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    this.fetchPosts(7);
  },
  comments: {PostForm},
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}
.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-top: 1rem;
}
</style>
