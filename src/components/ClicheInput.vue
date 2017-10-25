<template>
  <div class="input-container">
    <input
      v-model="newClicheText"
      @keyup.enter="emitCliche"
      @click="newClicheText = '', hasError = false"
      :class="['cliche-input', hasError ? 'error' : '']"
      type="text"
      placeholder="">
    <button @click="emitCliche" class="cliche-add">Add Cliché</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newClicheText: 'Tell everyone what I think about Breaking Bad',
      hasError: false
    }
  },
  methods: {
    emitCliche() {
      if(this.newClicheText === '') {
        this.newClicheText = 'Submitting without typing anything is so cliché';
        this.hasError = true;
      } else {
        this.hasError = false;
        this.$emit('add', this.newClicheText);
        this.newClicheText = '';
      }
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

.cliche-input.error {
  color: #f03e3e;
  font-style: italic;
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
