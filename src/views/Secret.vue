<template>
  <div class="secret">
    <h1>{{ message }}</h1>
    <button>Don't click me</button>
  </div>
</template>

<style></style>

<script>
export default {
  data: function () {
    return {
      message: "Welcome to the secret page",
    };
  },
  created: function () {},
  methods: {},
};
</script>
