<template>
  <div class="subreddits container">
    <h2>{{category | capitalize}}</h2>
    <ul class="item-list">
      <li v-for="subreddit in subreddits">
        <subreddit :item="subreddit"></subreddit>
      </li>
    </ul>
  </div>
</template>


<script>
import Subreddit from "./Subreddit";
export default {
  name: "subreddits",
  components: {
    Subreddit
  },
  props: ["category"],
  data() {
    return {
      subreddits: []
    };
  },
  created() {
    this.$http
      .get("https://www.reddit.com/r/" + this.category + "/top.json?limit=5")
      .then(res => {
        this.subreddits = res.data.data.children;
      });
  },
  filters: {
    capitalize(val) {
      if (!val) return "";
      val = val.toString();
      return val.charAt(0).toUpperCase() + val.slice(1);
    }
  }
};
</script>


<style scoped>
.container {
  max-width: 600px;
  margin: 30px auto;
  background: #fff;
  box-shadow: 0 0 3px #ccc;
}

.subreddits {
  min-width: 400px;
  padding: 25px 45px;
}
.subreddits h2 {
  font-size: 20px;
  margin-bottom: 10px;
  margin-top: 0;
}
.subreddits .item-list {
  border-top: 1px solid #ccc;
  padding-top: 20px;
  list-style: none;
}
.subreddits .item-list li {
  margin-bottom: 20px;
}
</style>

