<template>
  <div id="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">

          <!--first-modal-->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">First modal show</button>
          <modals-component title="FirstModal" v-show="modalFirst" @close="modalFirst = false">
          <div slot="bodyBox">
            <p>Text area</p>
            <button class="btn btnSecondary" @click="modalFirst = !modalFirst">Well done</button>
          </div>
          </modals-component>

          <!--second-modal-->
          <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Second modal show</button>
          <modals-component
          title="Second modal form"
          v-show="modalSecond.show"
          @close="modalSecond.show = false"
          >
          <div slot="bodyBox">
            <form action="" @submit.prevent="submitSecondForm">
              <label for="">Name:</label>
              <input type="text" v-model="modalSecond.name">
              <label for="">Email:</label>
              <input type="email" v-model="modalSecond.email">
              <button class="btn btnSecondary" >Submit/Send</button>
            </form>
          </div>
          </modals-component>

        </div>
      </section>
    </div>
  </div>
</template>

<script>
import ModalsComponent from "./components/ModalsComponent.vue";

export default {
  name: "App",
  components: { ModalsComponent },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show:false,
        name: '',
        email: ''
      }
    };
  },
  methods:{
    submitSecondForm(){
      console.log(`Hello & welcome ! ${this.modalSecond.name}, ${this.modalSecond.email} `);
      this.modalSecond.name = '';
      this.modalSecond.email = '';
      this.modalSecond.show = false;
    }
  }
};
</script>
<style>
.modal-enter{
  opacity: 0;
}
.modal-leave-active{
  opacity: 0;
}
.modal-enter .modal-content,
.modal-leave-active .modal-content{
  transform: scale(2.92s)
}
</style>
