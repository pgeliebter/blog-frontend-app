<template>
  <div class="posts-new">
    <h1>{{ message }}</h1>
    <form class="flex-down" v-on:submit.prevent="newPost()">
      <input type="text" placeholder="Title" v-model="postParams.title" />
      <input type="text" style="font-family: arial" placeholder="Body" v-model="postParams.body" />
      <input type="text" placeholder="Image URL" v-model="postParams.image_url" />
      <input type="submit" value="submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome Crumb Cake",
      postParams: {},
    };
  },
  created: function () {},
  methods: {
    newPost: function () {
      axios.post("/posts", this.postParams).then((response) => {
        this.$router.push("/posts");
        console.log(response.data);
      });
    },
  },
};
</script>

<style>
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
