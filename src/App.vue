<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/posts">Posts</router-link>
      |
      <router-link to="/posts/new">New Post</router-link>
    </div> -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary sticky-top">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNavDropdown"
          aria-controls="navbarNavDropdown"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavDropdown">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="/">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/posts">Posts</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/posts/new">New Post</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/about">About</a>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdownMenuLink"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                User
              </a>
              <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                <li v-if="!isLoggedIn()"><a class="dropdown-item" href="/login">Login</a></li>
                <li v-if="isLoggedIn()"><a class="dropdown-item" href="/logout">Logout</a></li>
                <li v-if="!isLoggedIn()"><a class="dropdown-item" href="/signup">Signup</a></li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Rockwell Extra Bold, Rockwell Bold, monospace !important;
  color: lightgrey !important;
  background-image: url("./assets/stardust.png");
  text-align: center;
}
</style>

<script>
export default {
  methods: {
    isLoggedIn: function () {
      if (localStorage.getItem("jwt")) return true;
      else return false;
    },
    getUserId: function () {
      if (localStorage.getItem("user_id")) return localStorage.getItem("user_id");
      else return "no user_id";
    },
  },
};
</script>
