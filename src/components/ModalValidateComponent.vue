<template>
  <modals-component title="Modal validate form comp" @close="$emit('close')">
    <button
      class="btn btnPrimary"
      @click="modalSecond.show = !modalSecond.show"
    >
      Second modal show
    </button>

    <div slot="bodyBox">
      <form @submit.prevent="">
        <div class="form-group" :class="{ 'form-group--error': $v.name.$error }">
          <label class="form__label">Name:</label>
          <input class="form__input" v-model.trim="name" @input="setName($event.target.value)"/>
        </div>

        <div class="error" v-if="!$v.name.required">Name is required</div>
        <div class="error" v-if="!$v.name.minLength">Name must have at least {{ $v.name.$params.minLength.min }} letters.</div>

        <div class="form-group" :class="{ 'form-group--error': $v.email.$error }">
          <label class="form__label">Email:</label>
          <input class="form__input" v-model.trim="email" />
        </div>

        <div class="error" v-if="!$v.email.required">Email is required</div>
        <div class="error" v-if="!$v.email.email">Email is not valid</div>
        <button class="btn btnSecondary" >Submit/Send</button>
      </form>
    </div>
  </modals-component>
</template>

<script>
import { required, minLength, email } from "vuelidate/lib/validators";

import ModalsComponent from "./ModalsComponent.vue";
export default {
  components: { ModalsComponent },
  data() {
    return {
      name: "",
      email: "",
    };
  },
  validations: {
    name: {
      required,
      minLength: minLength(4),
    },
    email: {
      required,
      email,
    },
  },
  methods: {
    setName(value) {
      this.name = value;
      this.$v.name.$touch();
    },
    setEmail(value) {
      this.email = value;
      this.$v.email.$touch();
    },
  },
};
</script>

<style scoped>
.error {
  color: orangered;
  font-size: 12px;
}
</style>