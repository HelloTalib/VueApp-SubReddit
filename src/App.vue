<template>
  <div id="app">
    <header>
      <h3>SubReddit</h3>
    </header>
    <subreddits category="food"></subreddits>
    <subreddits category="animals"></subreddits>
    <subreddits category="funny"></subreddits>
    <subreddits category="movies"></subreddits>
    <subreddits category="comedy"></subreddits>
  </div>
</template>

<script>
import Subreddits from "./components/Subreddits";
export default {
  name: "app",
  components: {
    Subreddits
  }
};
</script>

<style>
body {
  font-family: arial;
  color: #666666;
  background-color: #f4f4f4;
  margin: 0;
  padding: 0;
}
a {
  text-decoration: none;
}
header {
  background-color: coral;
  color: #fff;
  padding: 10px;
  text-align: center;
}
</style>
