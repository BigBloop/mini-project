<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__handle">@{{ user.username }}</h1>
      <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
      <div class="user-profile__follower-count">
        <strong>Followers: </strong>{{ followers }}
      </div>
    </div>
    <div class="user-profile__twoots-wrapper">
      <twoot-item
        v-for="twoot in user.twoots"
        :key="twoot.id"
        :username="user.username"
        :twoot="twoot"
        @favorite="toggleFavorite"
      />
    </div>
  </div>
</template>

<script>
import TwootItem from "./TwootItem.vue";
export default {
  name: "App",
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "MrMosna",
        firstName: "Marco",
        lastName: "Mosna",
        email: "mmosna404@gmail.com",
        isAdmin: true,
        twoots: [
          { id: 1, content: "Twotter is amooozing!" },
          { id: 2, content: "Don't forget to exercise! " },
        ],
      },
    };
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`);
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    toggleFavorite(id) {
      console.log(`Favorite Tweet #${id}`);
    },
  },
  components: {
    TwootItem,
  },
};
</script>

<style>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  padding: 50px 5%;
  gap: 50px;
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  padding: 20px;
  background-color: white;
  border-radius: 4px;
  border: 1px solid #dfe3e8;
}
.user-profile__admin-badge {
  background: rgb(170, 69, 162);
  color: white;
  border-radius: 5px;
  padding: 4px;
  margin-right: auto;
}
.user-profile__twoots-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 10px;
}
</style>
