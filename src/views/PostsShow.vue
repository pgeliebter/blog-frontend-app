<template>
  <div class="posts-new">
    <h1>{{ message }}</h1>
    <div class="flex-down">
      <h2>{{ post.title }}</h2>
      <div class="post-image-body">
        <span class="post-image"><img v-bind:src="post.image" /></span>
        <span class="post-body">{{ post.body }}</span>
      </div>
      <router-link v-if="$parent.getUserId() == post.user_id" to="`/posts/${post.id}/edit`">
        <button>Fuggehdaboutit</button>
      </router-link>
      <router-link to="/posts">Go back to all da posts</router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to the future of blogs:",
      post: {},
    };
  },
  created: function () {
    axios.get(`/posts/${this.$route.params.id}`).then((response) => {
      console.log(response);
      this.post = response.data;
      console.log(this.$parent.getUserId());
    });
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
  flex-direction: column;

  justify-content: space-between;
}
.flex-down * {
  margin: 10px;
}
</style>
