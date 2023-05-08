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
      <input v-model="counterData.title" type="text" />
    </div>
  </div>
</template>

<script setup>
import { reactive, computed, watch } from "vue";

// const counter = ref(0),
//   counterTitle = ref("My Counter");

// non reactive data
const appTitle = "My Amazing counter App";

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
</script>

<!-- 
<script>
export default{
computed: {
  myComputedProperty (){
    // prform logic based on a data property
    return 'my result'
  }
}
}
</script> -->

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
