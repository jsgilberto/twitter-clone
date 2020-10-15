<template>
  <b-container>

    <b-row>
      <b-col cols="4">
        <b-card
          :title="'@' + user.username"
          tag="article"
          class="mb-2"
        >
          <b-card-text>
            {{ user.email }} <br>
            <b-badge variant="info" v-if="user.isAdmin">Admin</b-badge> <br>
            <strong>Followers: </strong> {{ followers }}
          </b-card-text>

          <NewTweet @new-tweet="createNewTweet"/>
        </b-card>
      </b-col>
      <b-col>
        <h3>Tweets</h3>
        <TweetItem 
          v-for="tweet in user.tweets" 
          :key="tweet.id" 
          :username="user.username" 
          :tweet="tweet"
          class="mb-2"
          @favorite="toggleFavorite"
        >
        </TweetItem>
      </b-col>
    </b-row>
    

    

  </b-container>
  
  
</template>

<script>
import TweetItem from './TweetItem'
import NewTweet from './NewTweet'

export default {
  name: 'UserProfile',
  components: { TweetItem, NewTweet },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'chinitodaman',
        firstName: 'Jesus',
        lastName: 'Alvarez',
        email: 'alv.mtz94@gmail.com',
        isAdmin: true,
        tweets: [
          { id: 1, content: 'Twitter is amazing!'},
          { id: 2, content: 'I feel very positive about Vue.js! '}
        ]
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: {
    followUser() {
      this.followers++;
    },
    toggleFavorite(id) {
      alert(`Favorite id #${id}`);
    },
    createNewTweet(form) {
      console.log(form);
      this.user.tweets.unshift(
        { id: this.user.tweets.length + 1, content: form.tweet}
      )
    }
  },
  mounted() {
    this.followUser();
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (newFollowerCount > oldFollowerCount)
        console.log(`${this.user.username} has gained a follower!`);
    }
  }
}
</script>

<style scoped>
.user-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>