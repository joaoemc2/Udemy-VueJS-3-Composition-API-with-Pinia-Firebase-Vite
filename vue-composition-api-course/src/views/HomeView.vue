<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>

    <h3>{{ counterData.title }}:</h3>

    <div>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>

    <p>This count is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input type="text" v-model="counterData.title" />
    </div>
  </div>
</template>

<script setup>
import {
  ref,
  reactive,
  computed,
  watch,
  // onBeforeMount,
  onMounted,
  // onBeforeUnmount,
  // onActivated,
  // onDeactivated,
  // onBeforeUpdate,
  // onUpdated,
} from "vue";

const appTitle = "Hello World";

onMounted(() => {
  console.log("onMounted");
});

const counterData = reactive({
  count: 0,
  title: "My Counter",
});

watch(
  () => counterData.count,
  (newCount) => {
    if (newCount === 20) {
      alert("Way to go! Yout made it to 20!!");
    }
  }
);

const oddOrEven = computed(() => {
  if (counterData.count % 2 == 0) return "even";
  else return "odd";
});

const increaseCounter = (amount, e) => {
  console.log(e);
  counterData.count += amount;
};
const decreaseCounter = (amount) => {
  counterData.count -= amount;
};

// onBeforeMount(() => {
//   console.log("onBeforeMount");
// });
// onMounted(() => {
//   console.log("onMounted");
// });
// onBeforeUnmount(() => {
//   console.log("onBeforeUnmount");
// });
// onActivated(() => {
//   console.log("onActivated");
// });
// onDeactivated(() => {
//   console.log("onDeactivated");
// });

// onBeforeUpdate(() => {
//   console.log("onBeforeUpdate");
// });
// onUpdated(() => {
//   console.log("onUpdated");
// });
</script>

<style scoped>
.home {
  text-align: center;
  padding: 20px;
}

.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 32px;
}
</style>