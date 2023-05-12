<template>
  <div class="modals">
    <h1>Modals</h1>

    <div>
      <label for=""> Show dark modals? </label>
      <input v-model="showDarkModals" type="checkbox" />
    </div>
    <pre>{{ showDarkModals }}</pre>
    <button @click="showModal = true">Show modal</button>

    <!-- @hideModal="showModal = false" -->
    <!-- :userData="userData" -->
    <component
      v-model="showModal"
      :is="showDarkModals ? ModalDark : Modal" 
      title="My modal title (via prop)"
    >
      <!-- <template #title> This is slot title </template> -->
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. At repudiandae
        est ea fugit necessitatibus voluptatum voluptate adipisci aspernatur
        ipsum doloribus.
      </p>
    </component>
  </div>
</template>

<script setup>
/*
imports
*/
import { ref } from "vue";
import Modal from "../components/Modal.vue";
import ModalDark from "../components/ModalDark.vue";

/*
props
*/
// const props = defineProps({
//   userData: {
//     type: Object,
//   },
// });

/*
modals
*/
const showDarkModals = ref(false);
const showModal = ref(false);
</script>

<style lang="scss" scoped></style>
