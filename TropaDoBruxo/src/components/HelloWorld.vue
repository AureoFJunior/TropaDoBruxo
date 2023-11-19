<template>
  <div>
    <label for="nameInput">Enter Name:</label>
    <input v-model="name" id="nameInput" type="text" placeholder="Type a name..." />
    <button @click="addName">Add Name</button>

    <div class="name-list">
      <h2>Names List:</h2>
      <ul>
        <li v-for="(name, index) in names" :key="index">{{ name }}<font-awesome-icon icon="fa-solid " style="float: right;"></font-awesome-icon></li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const name = ref('');
    const names = ref<string[]>([]);

    const addName = () => {
      if (name.value.trim() !== '') {
        names.value.push(name.value);
        name.value = '';
      }
    };

    return {
      name,
      names,
      addName,
    };
  },
});
</script>

<style scoped>
.name-list {
  margin-top: 20px;
  border: 1px solid #ccc;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

label {
  font-size: 20px;
  margin-bottom: 5px;
  display: block;
}

input {
  padding: 8px;
  font-size: 14px;
  width: 100%;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
  background-color: transparent;
  color: whitesmoke;
}

button {
  padding: 10px;
  font-size: 16px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 12px;
  font-size: 16px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  color: whitesmoke;
}

</style>
