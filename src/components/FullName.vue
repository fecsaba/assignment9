<template>
  <div>
    <b-form-group label="Enter your first name" label-for="first_name">
      <b-form-input
        id="first_name"
        :value="firstName"
        @input="nameChanged(true, $event)"
      />
    </b-form-group>
    <b-form-group label="Enter your last name" label-for="last_name">
      <b-form-input
        id="last_name"
        :value="lastName"
        @input="nameChanged(false, $event)"
      />
    </b-form-group>
  </div>
</template>

<script>
export default {
  name: "FullName",
  props: ["value"],
  computed: {
    firstName() {
      return this.value.split(" ")[0];
    },
    lastName() {
      return this.value.split(" ")[1];
    }
  },
  methods: {
    nameChanged(isFirst, event) {
      console.log("event: " + event);
      let name = "";
      if (isFirst) {
        name = event + " " + this.lastName;
      } else {
        name = this.firstName + " " + event;
      }
      this.value = name;

      this.$emit("input", this.value);
    }
  }
};
</script>

<style scoped />
