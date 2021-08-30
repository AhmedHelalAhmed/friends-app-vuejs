<template>
  <section>
    <form @submit.prevent="submitData">
      <div>
        <label> Name: </label>

        <input v-model="name" type="text" />
      </div>
      <div>
        <label> Phone: </label>

        <input v-model="phone" type="tel" />
      </div>
      <div>
        <label> E-mail: </label>

        <input v-model="email" type="email" />
      </div>

      <div>
        <button type="submit">Add contact</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      name: "",
      phone: "",
      email: "",
    };
  },
  methods: {
    submitData() {
      this.$emit("add-contact", {
        id: new Date().toISOString(),
        name: this.name,
        phone: this.phone,
        email: this.email,
        isFavorite: false,
      });
      this.resetForm();
    },
    resetForm() {
      this.name = "";
      this.phone = "";
      this.email = "";
    },
  },
};
</script>