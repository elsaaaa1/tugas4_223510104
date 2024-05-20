<template>
  <div class="child">
    <h2>Child Component</h2>
    <button @click="sendDataToParent">Kirim Data ke Parent</button>
    <GrandChildComponent @grandchild-event="handleGrandchildEvent"/>
    <slot></slot>
  </div>
</template>

<script>
import GrandChildComponent from './GrandChildComponent.vue';

export default {
  components: {
    GrandChildComponent
  },
  methods: {
    sendDataToParent() {
      const data = prompt('Masukkan data untuk dikirim ke Parent:', '');
      if (data) {
        this.$emit('child-event', data);
      }
    },
    handleGrandchildEvent(data) {
      this.$emit('child-event', data);
    }
  }
};
</script>

<style scoped>
.child {
  border: 2px solid #2196F3;
  padding: 20px;
  margin: 10px;
}
button {
  background-color: #f27cc5;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}
button:hover {
  background-color: #f68bdb;
}
</style>
