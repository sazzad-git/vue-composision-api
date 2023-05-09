<template>
  <div class="home">
    <h1>{{ appTitle }}</h1>
    <h3>{{ counterData.title }}:</h3>
    <div>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>

    <p>This counter is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit COunter title</h4>
      <input v-model="counterData.title" type="text" v-autofocus />
    </div>
  </div>
</template>

<script setup>
/*
imports
*/
import { vAutofocus } from "@/directives/vAutofocus";
import {
  reactive,
  computed,
  watch,
  onBeforeMount,
  onMounted,
  onBeforeUnmount,
  onUnmounted,
  onActivated,
  onDeactivated,
  onBeforeUpdate,
  onUpdated,
} from "vue";

// const counter = ref(0),
//   counterTitle = ref("My Counter");

/*
App title
*/
// non reactive data
const appTitle = "My Amazing counter App";

onMounted(() => {
  console.log("Do stuff related to App title");
});

/*
counter
*/
// reactive data
const counterData = reactive({
  count: 0,
  title: "My Counter",
});

// computed property
const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return "even";
  return "odd";
});

// Watch
watch(
  () => counterData.count,
  (newCount, oldCount) => {
    if (newCount === 20) {
      alert("Way to go! You made it ti 20!!");
    }
  }
);

const increaseCounter = (amount, e) => {
  console.log(e);
  counterData.count += amount;
};
const decreaseCounter = (amount) => {
  counterData.count -= amount;
};

onMounted(() => {
  console.log("Do stuff related to counter");
});

/*
directives
*/
// const vAutofocus = {
//   mounted: (el) => {
//     el.focus();
//   },
// };

// multiple hooks

// count er man change korar por
// onBeforeUpdate, onUpdate
/*
onBeforeUpdate(() => {
  console.log("onBeforeUpdate");
});
onUpdated(() => {
  console.log("onUpdated");
});
*/

// page change korar por
// Mount unmount
/*
onBeforeMount(() => {
  console.log("onBeforeMount");
});
onMounted(() => {
  console.log("onMounted");
});
onBeforeUnmount(() => {
  console.log("onBeforeUnmount");
});
onUnmounted(() => {
  console.log("onUnmounted");
});
*/

// page change korar por je kono ek page active hoy
// onActivated, onDeactivated
/*
onActivated(() => {
  console.log("onActivated");
});
onDeactivated(() => {
  console.log("onDeactivated");
});
*/
</script>

<!-- 
<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  computed: {
    myComputedProperty() {
      // perfprm logic based on a data property
      return "my result";
    },
  },
  watch: {
    count(newCOunt, oldCount) {
      if (newCOunt === 20) alert("your counter is 20");
    },
  },
  directives: {
    autofocus: {
      mounted(el) {
        el.focus();
      },
    },
  },
};
</script>
  -->

<style lang="scss" scoped>
.home {
  text-align: center;
  padding: 20px;
  .btn,
  .counter {
    font-size: 40px;
    margin: 10px;
  }
  .edit {
    margin-top: 60px;
  }
}
</style>
