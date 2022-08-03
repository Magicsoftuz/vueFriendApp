<template>
  <section>
    <form @submit.prevent="addFriend">
      <label>Name:</label>
      <input v-model="enteredName" type="text" />
      <label>Phone</label>
      <input v-model="enteredPhone" type="text" />
      <label>Email</label>
      <input v-model="enteredEmail" type="text" />
      <button>Submit</button>
    </form>
  </section>
</template>

<script>
export default {
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
    };
  },
  emit: ["add-friend"],
  methods: {
    addFriend() {
      this.$emit(
        "add-friend",
        this.enteredName,
        this.enteredPhone,
        this.enteredEmail
      );
    },
  },
};
</script>

<style></style>
