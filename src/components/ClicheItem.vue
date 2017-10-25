<template>
  <li @click="checked = !checked" :class="['cliche-item', checked ? 'completed' : '']">
    <input v-model="checked" type="checkbox">
    <p>{{ cliche.text }}</p>
    <button @click.stop="$emit('delete', cliche.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    cliche: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      checked: this.cliche.checked
    }
  }
}
</script>

<style>
.cliche-item {
  display: flex;
  align-items: center;
  padding: 15px 20px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
  list-style: none;
  cursor: pointer;
}

.cliche-item:last-of-type {
  border-bottom: none;
}

.cliche-item p {
  flex-grow: 1;
  margin: 0;
  padding: 0 10px;
  text-align: left;
}

.cliche-item button {
  align-self: stretch;
  padding: 0 8px;
  border: none;
  background-color: #f03e3e;
  color: #fff;
  line-height: 1.6em;
  cursor: pointer;
  transition: transform 200ms ease;

  will-change: transform;
}

.completed p {
  color: #ced4da;
  text-decoration: line-through;
}

.cliche-item button:hover {
  transform: scale(1.1);
}
</style>
