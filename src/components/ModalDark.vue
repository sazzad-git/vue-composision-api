<template>
  <!-- <teleport to=".modals-container"> -->
  <div v-if="modelValue" class="modal-dark">
    <!-- <h1><slot name="title" /></h1> -->
    <h1>{{ title }}</h1>
    <slot />
    <button @click="$emit('update:modelValue')">Hide modal</button>
    <!-- <button @click="$emit('hideModal')">Hide modal</button> -->
  </div>
  <!-- </teleport> -->
</template>

<script setup>
/*
  imports
  */
import { useSlots } from "vue";
const slots = useSlots();

/*
  props
  */
const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false,
  },
  title: String,
  default: "No title specified",
});

/*
  emits
  */
const emit = defineEmits(["update:modelValue", "hideModal"]);
</script>

<style lang="scss" scoped>
.modal-dark {
  background: #333;
  color: white;
  padding: 10px;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
.modals-container {
  position: initial;
}
</style>
