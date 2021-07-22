<template>
  <div class="posts-edit">
    <h1>{{ message }}</h1>
    <form class="flex-down" v-on:submit.prevent="updatePost()">
      <input type="text" v-model="currentPostParams.title" />
      <input type="text" style="font-family: arial" v-model="currentPostParams.body" />
      <input type="text" v-model="currentPostParams.image" />
      <input type="submit" value="submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome Affagatto",
      currentPostParams: {},
    };
  },
  created: function () {
    axios.get(`/posts/${this.$route.params.id}`).then((response) => {
      console.log(response);
      this.currentPostParams = response.data;
    });
  },
  methods: {
    updatePost: function () {
      axios.patch(`/posts/${this.$route.params.id}`, this.currentPostParams).then((response) => {
        this.$router.push(`/posts/${response.data.id}`);
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
