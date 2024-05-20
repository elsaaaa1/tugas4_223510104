<template>
  <div class="parent">
    <h1>Parent Component</h1>
    <form @submit.prevent="addData">
      <input v-model="newData" placeholder="Masukkan data baru" required />
      <button type="submit">Tambahkan Data</button>
    </form>
    <ul>
      <li v-for="(item, index) in childData" :key="index">{{ item }}</li>
    </ul>
    <ChildComponent @child-event="handleChildEvent">
      <template v-slot:default>
        <p>Ini adalah konten dari parent yang dimasukkan melalui slot.</p>
        <p>Ellsya Putri Ananda</p>
      </template>
    </ChildComponent>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: {
    ChildComponent
  },
  data() {
    return {
      newData: '',
      childData: []
    };
  },
  methods: {
    addData() {
      this.childData.push(this.newData);
      this.newData = '';
    },
    handleChildEvent(data) {
      this.childData.push(data);
    }
  }
};
</script>

<style scoped>
.parent {
  border: 2px solid #4CAF50;
  padding: 20px;
  margin: 10px;
}
form {
  margin-bottom: 10px;
}
input {
  padding: 5px;
  margin-right: 10px;
}
button {
  background-color: #76eab8;
  color: white;
  border: none;
  padding: 5px 10px;
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
  background: #e0f7fa;
  margin: 5px 0;
  padding: 5px;
  border: 1px solid #4CAF50;
}
</style>
