<template>
  <li>
    <h2>{{ name }} {{ best ? "(This the best friend)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <hr />
    <button @click="toggleBestFriend">
      {{ best ? "Remove" : "Add" }} best Friend
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ email }}
      </li>
    </ul>
    <button @click="deleteFriend">Delete Friend</button>
  </li>
</template>

<script>
export default {
  // props: ["name", "phone", "email", "theBestFriend"],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String, //Number, //Boolean, //Object, //Array, // Date
      required: true,
    },
    phone: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
    best: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  // emit: ["change-best"],
  emit: {
    "change-best": function (val) {
      if (val) {
        return true;
      } else {
        console.log("Id not found");
        return false;
      }
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleBestFriend() {
      this.$emit("change-best", this.id);
    },
    deleteFriend() {
      this.$emit("delete-friend", this.id);
    },
  },
};
</script>
