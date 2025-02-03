<template>
  <div id="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">First modal show</button>
          <modals-component title="FirstModal" v-show="modalFirst" @close="modalFirst = !modalFirst">
          <div slot="bodyBox">
            <p>Text area</p>
            <button class="btn btnSecondary" @click="modalFirst = !modalFirst">Well done</button>
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
    };
  },
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
