<template>
  <div class="container">
    <!-- <div class="user-profile">
      <div class="user-profile__user-panel">
        <h1 class="user-profile__username">@{{ user.username }}</h1>
        <div class="user-profile__follower-count">
          <strong>Followers:</strong> {{ followers }}
        </div>
      </div>
    </div> -->

    <h1>Profile</h1>
    <b-card
      :title="'@' + user.username"
      tag="article"
      class="mb-2"
    >
      <b-card-text>
        {{ user.email }} <br>
        <strong>Followers: </strong> {{ followers}}
      </b-card-text>

      <b-button href="#" variant="primary" @click="followUser" >Follow</b-button>
    </b-card>
  </div>
  
  
</template>

<script>
export default {
  name: 'UserProfile',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'chinitodaman',
        firstName: 'Jesus',
        lastName: 'Alvarez',
        email: 'alv.mtz94@gmail.com',
        isAdmin: true
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