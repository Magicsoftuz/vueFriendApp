<template>
  <li>
    <h2>{{ friends.name }} {{ changeFriend ? "Best Friend" : "" }}</h2>
    <button @click="changeToggle">Show Details</button>
    <button @click="clickBtn(friends)">Best Friend</button>
    <ul v-if="toggleInfo">
      <li><strong>Phone:</strong> {{ friends.phone }}</li>
      <li><strong>Email:</strong> {{ friends.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: ["friends", "best", "index", "info"],
  data() {
    return {
      message: "Hello Component",
      toggleInfo: true,
      changeFriend: this.best,
    };
  },
  methods: {
    changeToggle() {
      this.toggleInfo = !this.toggleInfo;
    },
    changeBest() {
      this.changeFriend = !this.changeFriend;
    },
    clickBtn(friends) {
      this.info(friends);
    },
  },
};
</script>

<style></style>
