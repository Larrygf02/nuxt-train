<template>
  <div>
    <h1>Posts</h1>
    <ul v-for="post in posts" v-bind:key="post.id">
      <Post :title="post.title" :id="post.id"></Post>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Post from "../../components/Post";
export default {
  data() {
    return {
      posts: []
    };
  },
  components: {
    Post
  },
  async created() {
    const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
    console.log(res);
    this.posts = res.data;
  }
};
</script>
