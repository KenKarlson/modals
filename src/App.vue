<template>
  <div id="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">First modal show</button>
          <modals-component title="FirstModal" v-if="modalFirst" @close="modalFirst = !modalFirst"/>
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
