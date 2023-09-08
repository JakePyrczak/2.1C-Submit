<script setup>
import {ref} from 'vue'

const item_id = ref(0)
const todo_item = ref('')
const todo_list = ref([])
const todo = ref(false)

function add_item() {
    todo_list.value.push({
        id: item_id.value++,
        item: todo_item.value,
        status: todo.value
    })

    todo_item.value = ""
}

function remove_item(i) {
    todo_list.value = todo_list.value.filter((t) => t != i)
}

</script>

<template>
  <div class="myDiv">
    <h1><b>Dynamic Todo List</b></h1>
    <br>
    <input type='text' v-model="todo_item" placeholder="Add a new item">
    <button @click="add_item">Add Item</button>
    <br>
    <br>
    <transition-group name='fade' tag='ol'>
      <li v-for="i in todo_list" :key="i.id" class="list-item">
        <div class="list-item-inner">
          <input type="checkbox" v-model="i.status" class="checkbox">
          <span :class="{ done: i.status }">{{ i.item }}</span>
          <button @click="remove_item(i)" class="delete-button">X</button>
        </div>
      </li>
    </transition-group>
    <h5 v-if="todo_list.length < 1">No List Items</h5>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
.myDiv {
  border: 5px outset limegreen;
  background-color: #333; /* Dark background color */
  text-align: center;
  padding: 60px;
  color: white;
}
.list-item {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  background-color: #444; /* List item background color */
  border-radius: 5px; /* Rounded corners */
  padding: 10px; /* Spacing inside list item */
  transition: background-color 0.2s ease-in-out; /* Smooth background color transition */
}
.list-item:hover {
  background-color: #555; /* Darker background on hover */
}
.list-item-inner {
  display: flex;
  align-items: center;
  width: 100%;
}
.checkbox {
  margin-right: 10px;
}
.list-item input[type='checkbox']:checked + span {
  color: #00cc00;
  font-weight: bold;
  text-decoration-color: #ff0000;
}
.delete-button {
  margin-left: auto;
  background-color: #ff5555; /* Red delete button */
  color: white;
  border: none;
  border-radius: 50%; /* Circular button */
  padding: 5px 10px;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out; /* Smooth background color transition */
}
.delete-button:hover {
  background-color: #ff0000; /* Darker red on hover */
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

</style>