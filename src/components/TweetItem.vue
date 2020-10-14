<template>
  <b-card class="tweet-item" @click="favoriteTweet(tweet.id)">
    <b-card-text>
      <p>{{ tweet.content }}</p>
      - <strong>{{ username }}</strong>
    </b-card-text>
  </b-card>
</template>

<script>
export default {
  name: 'TweetItem',
  props: {
    username: {
      type: String,
      required: true
    },
    tweet: {
      type: Object,
      required: true
    }
  },
  methods: {
    favoriteTweet(id) {
      this.$emit('favorite', id)
    }
  }
}
</script>

<style scoped>
.tweet-item {
  cursor: pointer;
  transition: all 0.25s ease;
}

.tweet-item:hover {
  transform: scale(1.05, 1.05);
}
</style>
