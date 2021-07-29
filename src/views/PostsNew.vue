<template>
  <div class="posts-new">
    <img v-if="status" :src="`https://http.cat/${status}`" />
    <h1>{{ message }}</h1>
    <form class="flex-down" v-on:submit.prevent="newPost()">
      <input type="text" placeholder="Title" v-model="postParams.title" />
      <input
        type="text"
        placeholder="Body"
        v-model="postParams.body"
        :class="{ red: postParams.body.split(` `).length > 5 }"
      />
      <small>{{ 6 - postParams.body.split(" ").length }} words remaining.</small>
      <input type="text" placeholder="Image URL" v-model="postParams.image" />
      <input type="submit" value="submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome Crumb Cake, make a new post!",
      postParams: { body: "" },
      errors: {},
      status: "",
    };
  },
  created: function () {},
  methods: {
    newPost: function () {
      axios
        .post("/posts", this.postParams)
        .then((response) => {
          this.$router.push("/posts");
          console.log(response.data);
        })
        .catch(
          (error) => (
            (this.errors = error.response.data.errors),
            (this.status = error.response.status),
            console.log(this.status, this.errors)
          )
        );
    },
  },
};
</script>

<style>
.red {
  background-color: red;
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
