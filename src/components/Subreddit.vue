<template>
  <div class="subreddit">
    <a
      :href="makeUrl(item.data.permalink)"
      :style="makeImage(item.data.thumbnail)"
      target="_blank"
      class="thumbnail"
    ></a>
    <div class="details">
      <a
        :href="makeUrl(item.data.permalink)"
        :title="item.data.title"
        target="_blank"
      >{{item.data.title | truncate}}</a>
      <br>
      <div class="stats">
        <i class="material-icons">thumbs_up_down</i>
        {{item.data.score}}
        <i class="material-icons">forum</i>

        
        {{item.data.num_comments}}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "subreddit",
  props: ["item"],
  methods: {
    makeImage: function(img) {
      return "background-image:url(" + img + ")";
    },
    makeUrl: function(permalink) {
      return "http://reddit.com/" + permalink;
    }
  },
  filters: {
    truncate(val) {
      var length = 50;
      if (val.length <= length) {
        return val;
      } else {
        return val.substring(0, length) + "....";
      }
    }
  }
};
</script>


<style scoped>
.subreddit {
  display: flex;
}
.subreddit .thumbnail {
  display: block;
  flex: 0 0 65px;
  height: 65px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  border-radius: 5px;
  margin-right: 12px;
}
.subreddit .thumbnail .title {
  font-size: 15px;
  margin-bottom: 5px;
  color: steelblue;
}
.subreddit .thumbnail .stats {
  font-size: 12px;
  margin-right: 4px;
  margin-top: 7px;
  display: inline-block;
  color: #666;
}
.subreddit .stats i {
  font-size: 10px;
  margin-right: 2px;
}
</style>
