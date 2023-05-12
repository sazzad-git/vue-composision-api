<template>
  <!-- <teleport to=".modals-container"> -->
  <div v-if="modelValue" class="modal">
    <!-- <h1><slot name="title" /></h1> -->
    <h1>{{ title }}</h1>
    <slot />
    <button @click="$emit('update:modelValue')">Hide modal</button>
    <div>Username is: {{ userData.username }}</div>
    <!-- <button @click="$emit('hideModal')">Hide modal</button> -->
    <!-- <div>username is: {{ userData.username }}</div> -->
  </div>
  <!-- </teleport> -->
</template>

<script setup>
/*
imports
*/
import { useSlots, inject } from "vue";
const slots = useSlots();

/*
props
*/
const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false,
  },
  title: {
    type: String,
    default: "No title specified",
  },
  // userData: {
  //   type: Object,
  // },
});

/*
emits
*/
// const emit = defineEmits(["hideModal"]);
const emit = defineEmits(["update:modelValue", "hideModal"]);

/*
user data 
*/
const userData = inject("userData");

/*
Handle button click
*/

/*
const handleButtonClick = () => {
  // emit("hideModal");
  emit("update:modelValue", false);
};
*/

// console.log(slots.title());
</script>

<style lang="scss" scoped>
.modal {
  background: beige;
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
