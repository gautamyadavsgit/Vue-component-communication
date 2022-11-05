<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? "(Favourite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="changeFavorite">Change</button>

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
    <button @click="$emit('delete-contact', id)">Delete</button>
  </li>
</template>

<script>
export default {
  //   props: [
  //     'name',
  //     'phoneNumber',
  //     'email',
  //     'isFavorite',
  // ],

  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
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
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emists: ["toggle-favorite","delete-contact"],
  // emits:{
  //   'toggle-favorite': function (id){
  //   if(id){
  //     return true;
  //   }else{
  //     console.warn('Id is missing !');
  //     return false;
  //   }
  //   }
  // },
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: "manuel",
        name: "Manuel Lorenz",
        phone: "0123 45678 90",
        email: "manuel@localhost.com",
      },
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    changeFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
  },
};
</script>
