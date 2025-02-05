<template>
  <div id="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!--first-modal-->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
            First modal show
          </button>
          <modals-component
            title="FirstModal"
            v-show="modalFirst"
            @close="modalFirst = false"
          >
            <div slot="bodyBox">
              <p>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit.
                Ratione dolor similique tempora cupiditate! Molestias ex earum
                suscipit aspernatur excepturi vel dignissimos, tempore beatae
                at, provident ipsa corporis mollitia laboriosam. Eveniet, alias
                nam earum eius provident id. Nesciunt accusamus dolores id
                eaque? Quos, nulla sequi. Culpa molestias tenetur sapiente
                voluptate magni id, non fugit voluptas facilis.
              </p>
              <button
                class="btn btnSecondary"
                @click="modalFirst = !modalFirst"
              >
                Well done
              </button>
            </div>
          </modals-component>

          <!--second-modal-->
          <button
            class="btn btnPrimary"
            @click="modalSecond.show = !modalSecond.show"
          >
            Second modal show
          </button>
          <modals-component
            title="Second modal form"
            v-show="modalSecond.show"
            @close="modalSecond.show = false"
          >
            <div slot="bodyBox">
              <form action="" @submit.prevent="submitSecondForm">
                <label for="">Name:</label>
                <input type="text" v-model="modalSecond.name" />
                <label for="">Email:</label>
                <input type="email" v-model="modalSecond.email" />
                <button class="btn btnSecondary">Submit/Send</button>
              </form>
            </div>
          </modals-component>

          <!--modal-validate-->
          <button
            class="btn btnPrimary"
            @click="modalValidate = !modalValidate"
          >
            Modal validate show
          </button>
          <modal-validate-component v-show="modalValidate" @close="modalValidate = false">
            
          </modal-validate-component>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import { required, minLenght, email } from "vuelidate/lib/validators";

import ModalsComponent from "./components/ModalsComponent.vue";
import ModalValidateComponent from "./components/ModalValidateComponent.vue";

export default {
  name: "App",
  components: { ModalsComponent, ModalValidateComponent },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: "",
        email: "",
      },
      modalValidate: false,
    };
  },
  validations: {
    name: {},
  },
  methods: {
    submitSecondForm() {
      console.log(
        `Hello & welcome ! ${this.modalSecond.name}, ${this.modalSecond.email} `
      );
      this.modalSecond.name = "";
      this.modalSecond.email = "";
      this.modalSecond.show = false;
    },
    submitValidateForm() {
      console.log(
        `Hello & welcome ! ${this.modalValidate.name}, ${this.modalValidate.email} `
      );
      this.modalValidate.name = "";
      this.modalValidate.email = "";
      this.modalValidate.show = false;
    },
  },
};
</script>
<style>
.modal-enter {
  opacity: 0;
}
.modal-leave-active {
  opacity: 0;
}
.modal-enter .modal-content,
.modal-leave-active .modal-content {
  transform: scale(2.92s);
}
</style>
