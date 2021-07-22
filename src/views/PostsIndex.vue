<template>
  <div class="posts-index">
    <h1>{{ message }}</h1>
    <form></form>

    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <div class="post-image-body">
        <span class="post-image"><img v-bind:src="post.image" /></span>
        <span class="post-body">{{ post.body }}</span>
      </div>
      <hr />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome Crumb Cake",
      posts: [1, 2, 3],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/posts").then((response) => {
        this.posts = response.data;
        console.log(response.data);
      });
    },
  },
};
</script>

<style>
.post-image-body {
  display: flex;
  align-items: center;
  padding: 10px;
  justify-content: space-between;
}
.post-image-body * {
  flex: 1 1 auto;
  text-align: center;

  margin: 5px;
}
.flex-down {
  display: flex;
  align-items: center;
  flex-direction: column-reverse;

  justify-content: space-between;
}
</style>
