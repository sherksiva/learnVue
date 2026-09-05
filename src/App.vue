<script setup>
  import { reactive, ref } from 'vue';

  // Counter Binding with reactive
  const counter = reactive({
    count: 0
  });

  // Message Binding with ref
  const message = ref('Hello World!')

  // Just to show that reactive and ref are reactive
  console.log(counter.count) // 0
  console.log(message.value) // Hello World!

  // Increment function to update the counter
  // It will trigger with v-on:click event on the button
  function increment() {
    // update component state
    alert('Incrementing the counter');
    counter.count++;
  }
  
  // For ClassName binding
  const messageClass = ref('color-red');
  const counterClass = ref('counter');
  const reflink = ref('ref-link');
  const wholeItem = ref('whole-item');

</script>

<template>
  <h1>Vue JS Learning:Path</h1>
  <div :class="wholeItem">
    <!-- 1. for class binding and reactive count, we can use the following code: -->
    <p :class="counterClass">Reactive count with class: {{ counter.count }}</p>
    <p :class="messageClass">Ref message with message Class: {{ message }}</p>
    <!-- 2. Counter Increase function-->
    <button v-on:click="increment">Increase Count</button>
    <!-- Reference link for Vue JS Documentation -->
    <div :class="reflink">
      Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
      documentation
    </div>
  </div>
</template>

<style scoped>
  .whole-item {
    width: 200vh;
    margin: 0 auto;
  }
  .color-red {
    color: red;
  }
  .counter {
    background-color: green;
    font-size: 20px;
    font-weight: 600;
    padding: 10px;
    font-style: italic;
  }
  .ref-link {
    font-size: 18px;
    border-top: 1px solid #ccc;
    padding-top: 10px;
    margin-top: 10px;
  }
</style>
