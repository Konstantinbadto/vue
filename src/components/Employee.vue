<template>
  <div class="employee">
    <h3>{{ name }}</h3>
    <p>Зарплата: {{ salary }}</p>
    <p>Возраст: {{ age }}</p>
    <h3>Элементы массива:</h3>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    <button @click="callFirstFunction">Вызвать первую функцию</button>
    <button @click="callSecondFunction">Вызвать вторую функцию</button>
    <button @click="emitEvent">Испустить событие</button>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    salary: {
      type: Number,
      required: true,
    },
    age: {
      type: Number,
      required: true,
    },
    items: {
      type: Array,
      required: true,
    },
    firstFunction: {
      type: Function,
      required: true,
    },
    secondFunction: {
      type: Function,
      required: true,
    },
  },
  methods: {
    callFirstFunction() {
      this.firstFunction();
    },
    callSecondFunction() {
      this.secondFunction();
    },
    emitEvent() {
      this.$emit('employee-clicked', this.name); // Испускаем событие с именем работника
    },
  },
};
</script>

<style scoped>
.employee {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}
</style>
