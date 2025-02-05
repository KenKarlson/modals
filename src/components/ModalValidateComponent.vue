<template>
<modals-component
            title="Modal validate form comp"
            @close="$emit('close')"
          >
          <button
            class="btn btnPrimary"
            @click="modalSecond.show = !modalSecond.show"
          >
            Second modal show
          </button>
            <div slot="bodyBox">
              <form action="" @submit.prevent="">
                <label for="">Name:</label>
                <input type="text" />
                <label for="">Email:</label>
                <input type="email"  />
                <button class="btn btnSecondary">Submit/Send</button>
              </form>
            </div>
          </modals-component>
</template>

<script>
import ModalsComponent from "./ModalsComponent.vue";
export default {
  components: { ModalsComponent},
};
</script>
