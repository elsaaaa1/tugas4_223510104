<template>
  <div class="grandchild">
    <h3>GrandChild Component</h3>
    <button @click="sendDataToChild">Kirim Data ke Child</button>
  </div>
</template>

<script>
export default {
  methods: {
    sendDataToChild() {
      const data = prompt('Masukkan data untuk dikirim ke Child:', '');
      if (data) {
        this.$emit('grandchild-event', data);
      }
    }
  }
};
</script>

<style scoped>
.grandchild {
  border: 2px solid #f381c0;
  padding: 20px;
  margin: 10px;
}
button {
  background-color: #7ad0eb;
  color: rgb(255, 255, 255);
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}
button:hover {
  background-color: #89d9f6;
}
</style>
