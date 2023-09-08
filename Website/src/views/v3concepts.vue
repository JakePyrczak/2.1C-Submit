<script setup>
import { ref } from "vue";

const textbox = ref("Editable Text");
const check_val = ref(true);
const check_multi = ref(["Deakin"]);
const pickbox = ref("Second");
const dropdown = ref("A");
const multi_choice = ref(["A"]);
const vIf = ref(true);
const vShow = ref(true);

// Conditional Rendering
const toggleRendering = () => {
  vIf.value = !vIf.value
}

// Form Input Handling
const checkNames = ["Deakin", "Monash", "Melbourne"];
const radioOptions = ["First", "Second", "Third"];
const selectOptions = ["A", "B", "C", "D", "E", "F"];
</script>

<template>
  <div class="myDiv">
    <h2>Text Input</h2>
    <input v-model="textbox" />
    <br />
    {{ textbox }}
    <br /><br />

    <h2>Checkbox</h2>
    <input type="checkbox" id="checkbox" v-model="check_val" />
    <label for="checkbox">Checked: {{ check_val }}</label>
    <br /><br />

    <h2>Multi Checkbox</h2>
    <div v-for="(name, index) in checkNames" :key="index">
      <input type="checkbox" :id="name" :value="name" v-model="check_multi" />
      <label :for="name" style="padding-right: 10px">{{ name }}</label>
    </div>
    <p>Checked names:
      <pre>{{ check_multi }}</pre>
    </p>
    <br />

    <h2>Radio Selection</h2>
    <div v-for="(option, index) in radioOptions" :key="index">
      <input type="radio" :id="option" :value="option" v-model="pickbox" />
      <label :for="option">{{ option }}</label>
      <br />
    </div>
    <span>Picked: {{ pickbox }}</span>
    <br /><br />

    <h2>Select Dropdown</h2>
    <select v-model="dropdown">
      <option disabled value="">Please select one</option>
      <option v-for="(option, index) in selectOptions" :key="index">{{ option }}</option>
    </select>
    <span style="padding-left: 10px">Selected: {{ dropdown }}</span>
    <br /><br />

    <h2>Multi Select</h2>
    <select v-model="multi_choice" multiple style="width: 100px">
      <option v-for="(option, index) in selectOptions" :key="index">{{ option }}</option>
    </select>
    <br />
    <span>Selected: {{ multi_choice }}</span>
    <br><br>

    <!-- Conditional Rendering Examples -->
    <h2>Conditional Rendering Examples</h2>
   
    <div v-if="vIf">This text is being shown using v-if</div>

    <div v-else>This is shown using v-else if the v-if statement is turned false</div><br>

    <button @click="toggleRendering">Toggle IF and ELSE rendering</button><br><br>

    <div v-show="vShow">This is shown using v-show, essentially a different way of conditional rendering</div><br>
  </div>
</template>

<style scoped>
.myDiv {
  border: 5px outset limegreen;
  background-color: #333; /* Dark background color */
  text-align: center;
  padding: 60px;
  color: white;
}
</style>