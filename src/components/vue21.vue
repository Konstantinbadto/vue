<template>
  <div>
    <h1>Список сотрудников</h1>
    <Employee
      v-for="employee in employees"
      :key="employee.id"
      :name="employee.name"
      :salary="employee.salary"
      :age="employee.age"
    />
    <ChildComponent :items="myArray" />
    <h1>Родительский компонент</h1>
    <p>Сообщение: {{ message }}</p>
    <ChildComponent
      :firstFunction="updateMessageToHello"
      :secondFunction="updateMessageToWorld"
    />
  </div>
</template>

<script>
import Employee from './Employee.vue';
import ChildComponent from './Employee.vue'; // ИСПРАВЛЕН ИМПОРТ

export default {
  components: {
    Employee,
    ChildComponent,
  },
  data() {
    return {
      employees: [
        { id: 1, name: 'Иван', salary: 50000, age: 30 },
        { id: 2, name: 'Петр', salary: 60000, age: 35 },
        { id: 3, name: 'Анна', salary: 70000, age: 28 },
      ],
      myArray: ['Элемент 1', 'Элемент 2', 'Элемент 3'],
      message: 'Начальное сообщение',
    };
  },
  methods: {
    updateMessageToHello() {
      this.message = 'Привет!';
    },
    updateMessageToWorld() {
      this.message = 'Мир!';
    },
  }, // ИСПРАВЛЕНА СТРУКТУРА
};
</script>
