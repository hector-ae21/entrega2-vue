<template>
  <div id="app">
    <h1>Vue 3 Reactivity Examples</h1>
    <div class="section">
      <h2>Ref and Reactive</h2>
      <button @click="increment">Increment Ref</button>
      <p>Ref counter: {{ countRef }}</p>
      <button @click="incrementReactive">Increment Reactive</button>
      <p>Reactive counter: {{ state.count }}</p>
    </div>
    <div class="section">
      <h2>Computed and Watch</h2>
      <button @click="incrementComputed">Increment Computed</button>
      <p>Doubled: {{ doubled }}</p>
    </div>
    <NumberCounter :initialCount="10" title="Main Counter"/>
  </div>
</template>

<script>
import { ref, reactive, computed, watch } from 'vue';
import NumberCounter from './components/NumberCounter.vue';

export default {
  name: 'App',
  components: {
    NumberCounter
  },
  setup() {
    // ref is used for primitive reactive state
    const countRef = ref(0);
    function increment() {
      countRef.value++;
    }

    // reactive is used for object reactive state
    const state = reactive({ count: 0 });
    function incrementReactive() {
      state.count++;
    }

    // computed property that calculates the double of the ref count
    const count = ref(0);
    const doubled = computed(() => count.value * 2);

    // Increment function for computed property
    function incrementComputed() {
      count.value++;
    }

    // watch effect to log changes in the computed property
    watch(count, (newValue, oldValue) => {
      console.log(`Count changed from ${oldValue} to ${newValue}`);
    });

    return { countRef, increment, state, incrementReactive, count, doubled, incrementComputed };
  }
};
</script>

<style>
#app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Arial', sans-serif;
}
.section {
  margin-bottom: 20px;
  padding: 10px;
  background-color: #f0f0f0;
  border-radius: 8px;
}
button {
  margin-top: 5px;
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #45a049;
}
p {
  margin: 5px 0;
}
</style>
