<template>
  <div class="twoot-item" @click="favoriteTwoot(twoot.id)">
    <div class="user-profile__twoot">
      <div class="twoot-item__user">@{{ username }}</div>
      <div class="twoot-item__content">
        {{ twoot.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TwootItem",
  props: {
    username: {
      type: String,
      required: true,
    },
    twoot: {
      type: Object,
      required: true,
    },
  },
  methods: {
    favoriteTwoot(id) {
      this.$emit('favorite', id)
    }
  }
};
</script>

<style>
.twoot-item {
  background-color: white;
  border-radius: 4px;
  border: 1px solid #dfe3e8;
  padding: 20px;
  box-sizing: border-box;
  cursor: pointer;
  transition: all 0.25s ease;
}
.twoot-item:hover {
  transform: scale(1.1);
}
.user-profile__twoot {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.twoot-item__user {
  font-weight: bold;
}
</style>
