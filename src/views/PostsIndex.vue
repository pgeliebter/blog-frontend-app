<template>
  <div class="posts-index">
    <div class="d-flex flex-column align-items-center">
      <div class="card mb-3" style="max-width: 540px" v-for="post in posts" :key="post.id">
        <div v-bind:class="{ hover: thisPost === post }" v-on:mouseover="thisPost = post">
          <router-link v-bind:to="`/posts/${post.id}`">
            <div class="row g-0">
              <div class="col-md-4">
                <img v-bind:src="post.image" class="img-fluid rounded-start" v-bind:alt="post.title" />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{ post.title }}</h5>
                  <p class="card-text"></p>
                  <p class="card-text"><small class="text-muted">Last updated never mins ago</small></p>
                </div>
              </div>
            </div>
          </router-link>
        </div>
      </div>
    </div>

    <!-- <h1>{{ message }}</h1>
    <form></form>

    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <div class="post-image-body">
        <span class="post-image"><img v-bind:src="post.image" /></span>
        <span class="post-body">{{ post.body }}</span>
      </div>
      <router-link v-bind:to="`/posts/${post.id}`">
        <button v-on:click="moreInfo()">More Info!</button>
      </router-link>

      <hr />
     </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome Crumb Cake",
      posts: [1, 2, 3],
      thisPost: {},
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
    moreInfo: function () {
      console.log("you found me!");
    },
  },
};
</script>

//
<style>
.hover {
  color: aquamarine;
  background-color: red;
}
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
