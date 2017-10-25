<template>
  <div class="input-container">
    <input
      v-model="newClicheText"
      @keyup.enter="emitCliche"
      @click="newClicheText = ''"
      class="cliche-input"
      type="text"
      placeholder="">
    <button @click="emitCliche" class="cliche-add">Add Cliché</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newClicheText: 'Tell everyone what I think about Breaking Bad'
    }
  },
  methods: {
    emitCliche() {
      this.$emit('add', this.newClicheText);
      this.newClicheText = '';
    }
  }
}
</script>

<style>
.input-container {
  display: flex;
  align-items: stretch;
  justify-content: space-between;
  margin-bottom: 20px;
}

.cliche-input {
  display: block;
  flex: 0 1 85%;
  padding: 15px 20px;
  outline: none;
  border: none;
  border-top: 1px solid rgba(0, 0, 0, 0.05);
  border-bottom: 1px solid rgba(0, 0, 0, 0.35);
  color: #495057;
}

.cliche-add {
  padding: 0 20px;
  outline: none;
  border: none;
  background-color: #15aabf;
  color: #fff;
  white-space: nowrap;
  transition: all 200ms ease;
}

.cliche-add:hover {
  background-color: #4c6ef5;
}

::-webkit-input-placeholder {
  color: rgba(0, 0, 0, 0.15);
}
::-moz-placeholder {
  color: rgba(0, 0, 0, 0.15);
}
:-ms-input-placeholder {
  color: rgba(0, 0, 0, 0.15);
}
:-moz-placeholder {
  color: rgba(0, 0, 0, 0.15);
}
</style>
