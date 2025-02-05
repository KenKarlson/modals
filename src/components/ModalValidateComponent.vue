<template>
  <modals-component
  titlel="Modal title"
  @close="$emit('close')">
  <div slot="body">
    <form @submit.prevent="submit">
      <label>Name:</label>
      <input v-bind="name">
      <label>Email:</label>
      <input v-bind="email">
      <button class="btn btnSecondary" >Submit/Send</button>
    </form>
  </div>
  </modals-component>
</template>

<script>
import {required, minLenght, email} from 'vuelidate/lib/validators'
import ModalsComponent from "./ModalsComponent.vue";

export default {
  components: { ModalsComponent },
  data() {
    return {
      name:'',
      email:''
    };
  },
  valitations: {
    name: {
      required,
      minLenght: minLenght(4)
    },
    email: {
      required,
      email
    }
  },
}
</script>


<style lang="scss" scoped>
//modal animate
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.modal__wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  transition: opacity 0.5s ease;
  z-index: 998;
  background-color: rgba(50, 70, 99, 0.3);
}

.modal-content {
  position: relative;
  max-width: 600px;
  padding: 20px 18px;
  background-color: #fff;
  border: 1px solid #dcdfe6;
  transition: all 0.3s ease;
  border-radius: 8px;
  z-index: 999;
  overflow: hidden;
  @media screen and (min-width: 900px) {
    min-width: 500px;
  }
}
.modal-header {
  display: flex;
  align-self: center;
  justify-content: space-between;
  padding-bottom: 20px;
  span {
    font-size: 24px;
  }
  .button-close {
    cursor: pointer;
  }
}
.modal-body {
  text-align: center;
}
</style>