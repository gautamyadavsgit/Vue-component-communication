<template>
  <form @submit.prevent="addContact">
    <div>
      <label>Name</label>
      <input type="text" v-model="name" />
    </div>
    <div>
      <label>Email</label>
      <input type="email" v-model="email" />
    </div>
    <div>
      <label>Phone</label>
      <input type="tel" v-model="phone" />
    </div>
    <div><button type="submit">Add Contact</button></div>
  </form>
</template>

<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      name: "",
      email: "",
      phone: "",
    };
  },
  methods: {
    addContact() {
      this.$emit("add-contact", this.name, this.email, this.phone);
    },
  },
};
</script>
