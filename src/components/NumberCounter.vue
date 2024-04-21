<template>
  <div class="counter">
    <h3>{{ title }}</h3>
    <button @click="increment">Increment</button>
    <p>Counter: {{ count }}</p>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'NumberCounter', // Component name should be multi-word to avoid conflicts
  props: {
    initialCount: Number,
    title: String
  },
  setup(props) {
    const count = ref(props.initialCount || 0); // Initialize counter from props
    const increment = () => {
      count.value++;
    };

    return { count, increment };
  }
};
</script>

<style scoped>
.counter {
  background-color: #e9e9e9;
  padding: 15px;
  border-radius: 5px;
}
h3 {
  color: #2c3e50;
}
button {
  padding: 8px 16px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 10px;
}
button:hover {
  background-color: #2980b9;
}
p {
  margin-top: 15px;
}
</style>
