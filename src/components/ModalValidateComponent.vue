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
        <div class="form-item" :class="{errorInput: $v.name.$error}">
          <label for="">Name:</label>
          <p class="errorText" v-if="!$v.name.$required">Name is required</p>
          <p class="errorText" v-if="!$v.name.$minLenght">Name is lenghts </p>
          <input v-bind="name" :class="{error: $v.name.$error}" @change="$v.name.$touch()" placeholder=""/>
        </div>
        
        <label for="">Email:</label>
        <input v-bind="email" />
        <button class="btn btnSecondary">Submit/Send</button>
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
};
</script>
