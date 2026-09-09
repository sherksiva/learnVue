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
    counter.count++;
  }

  // For Toggle function 
  function toggleCondition () {
    toggle.value = !toggle.value;
  }

  // For Todo Form
  const todoList = ref([]);

  function addList() {
    if (todoInput.value.trim() !== '') {
      todoList.value.push(todoInput.value);
      todoInput.value = '';
    }
  }

  function deleteTodoItem(item) {
    todoList.value = todoList.value.filter((t) => t !== item)
  }

  
  // For ClassName binding
  const messageClass = ref('color-red');
  const counterClass = ref('counter');
  const reflink = ref('ref-link');
  const wholeItem = ref('whole-item');
  const borderTop = ref('border-top');
  // For input field binding
  const input_text = ref('');
  // For toggle value binding
  const toggle = ref(true);
  // For Todo input field binding
  const todoInput = ref('');

</script>

<template>
  <h1 :style="{ textAlign: 'center' }">Vue JS Learning</h1>
  <div :class="wholeItem">
    <!-- Class 1 -->
    <div>
      <h3>1. Reactive Bindings / Ref Bindings</h3>
      <!-- 1. for class binding and reactive count, we can use the following code: -->
      <p :class="counterClass">Reactive count with class: {{ counter.count }}</p>
      <p :class="messageClass">Ref message with message Class: {{ message }}</p>
      <!-- 2. Counter Increase function-->
      <button v-on:click="increment">Increase Count</button>

      <h3>2. Form Bindings</h3>
      <input type="text" v-model="input_text" placeholder="Type something..." />
      <p>Input Message: {{ input_text }}</p>

      <h3>3. Conditional Rendering</h3>
      <button @click="toggleCondition">Toggle</button>
      <h5 v-if="toggle">Initial Hi</h5>
      <h5 v-else>Toggle hi</h5>
      <!-- We can write what ever div, etc for v-else for sample-->
        <!-- <div v-else >
          <div>
            <h5>Toggle Hi</h5>
          </div>
        </div> -->

      <h3>5. Todo Form</h3>

      <form @submit.prevent="addList">
        <input type="text" v-model="todoInput" placeholder="Add a todo item..." />
        <button type="submit">Add</button>
        <ul>
          <li v-for="(item, index) in todoList" :key="index">{{ item }} <button @click="deleteTodoItem(item)">x</button></li>
        </ul>
        <span v-if="todoList.length === 0">No todo items yet.</span>
      </form>

      <!-- Reference link for Vue JS Documentation -->
      <div :class="[reflink, borderTop]">
        Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
        documentation
      </div>
    </div>
  </div>
</template>

<style scoped>
  .whole-item {
    width: 200vh;
    margin: 0 auto;
    border-right: 1px solid #cccccc;
    border-left: 1px solid #cccccc;
    padding: 10px;
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

  .border-top {
    border-top: 1px solid #ccc;
  }

  h3 {
    color: #782dd2;
    border-bottom: 1px solid #ccc;
    padding-bottom: 10px;
  }
</style>
