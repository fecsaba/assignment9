<!-- Exercise 1 -->
<!-- Create a Signup Form where you retrieve the following Information -->
<!-- Full Name (First Name + Last Name) -->
<!-- Mail -->
<!-- Password -->
<!-- Store Data? Yes/No -->

<!-- Exercise 2 -->
<!-- Only display the Form if it has NOT been submitted -->
<!-- Display the Data Summary ONCE the Form HAS been submitted -->

<!-- Exercise 3 -->
<!-- Edit the Example from above and create a custom "Full Name" Control -->
<!-- which still holds the First Name and Last Name Input Field -->
<template>
  <b-container>
    <b-row align-h="center" v-if="!submitted">
      <b-col cols="10">
        <b-form>
          <app-full-name v-model="person.fullName"></app-full-name>
          <b-form-group label="Enter your email address" label-for="email_addr">
            <b-form-input id="email_addr" v-model="person.email" trim />
          </b-form-group>
          <b-form-group label="Enter your Password" label-for="email_addr">
            <b-form-input
              id="password"
              type="password"
              v-model="person.password"
              trim
            />
          </b-form-group>
          <div class="text-center">
            <b-form-group label="Store data?">
              <b-form-radio-group
                v-model="selected"
                :options="options"
                name="radio-inline"
              >
              </b-form-radio-group>
            </b-form-group>
            <div class="mt-3">
              Selected: <strong>{{ selected }}</strong>
            </div>

            <b-button class="mt-5" variant="primary mt5"
              @click="submitted = true">Submit</b-button>
          </div>
          <hr />
        </b-form>
      </b-col>
    </b-row>
    <b-row align-h="center" v-if="submitted">
      <b-col cols="8">
        <b-card title="Your data" tag="article" class="mt-5">
          <b-card-text>Full name: {{ person.fullName }} </b-card-text>
          <b-card-text>Email: {{ person.email }} </b-card-text>
          <b-card-text>Password: {{ person.password }} </b-card-text>
          <b-card-text>Store in Database?: {{ selected }} </b-card-text>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import FullName from "@/components/FullName";

export default {
  name: "app",
  components: {
    appFullName: FullName
  },
  data: function() {
    return {
      person: {
        fullName: "Who AmI",
        email: "",
        password: ""
      },

      selected: "No",
      options: [
        { text: "Yes", value: "Yes" },
        { text: "No", value: "No" }
      ],
      submitted: false
    };
  }
};
</script>

<style />
