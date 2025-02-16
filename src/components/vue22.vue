<template>
    <div>
      <h1>Список сотрудников</h1>
      <Employee
        v-for="employee in employees"
        :key="employee.id"
        :id="employee.id"
        :name="employee.name"
        :salary="employee.salary"
        :age="employee.age"
        @delete-employee="handleDeleteEmployee"
        @update-employee="handleUpdateEmployee"
      />

      <h2>Добавить нового сотрудника</h2>
      <form @submit.prevent="addEmployee">
        <label>Имя:</label>
        <input type="text" v-model="newEmployee.name" required />

        <label>Зарплата:</label>
        <input type="number" v-model="newEmployee.salary" required />

        <label>Возраст:</label>
        <input type="number" v-model="newEmployee.age" required />

        <button type="submit">Добавить</button>
      </form>
    </div>
  </template>

  <script>
  import Employee from './Employee.vue';

  export default {
    components: {
      Employee,
    },
    data() {
      return {
        employees: [
          { id: 1, name: 'Иван', salary: 50000, age: 30 },
          { id: 2, name: 'Петр', salary: 60000, age: 35 },
          { id: 3, name: 'Анна', salary: 70000, age: 28 },
        ],
        newEmployee: {  // Объект для данных нового сотрудника
          name: '',
          salary: null,
          age: null,
        },
      };
    },
    methods: {
      handleDeleteEmployee(employeeId) {
        this.employees = this.employees.filter(employee => employee.id !== employeeId);
      },
      handleUpdateEmployee(updatedEmployee) {
        const index = this.employees.findIndex(employee => employee.id === updatedEmployee.id);
        if (index !== -1) {
          this.employees.splice(index, 1, updatedEmployee);
        }
      },
      addEmployee() {
        if (this.newEmployee.name && this.newEmployee.salary && this.newEmployee.age) {
          const newId = this.employees.length > 0 ? Math.max(...this.employees.map(e => e.id)) + 1 : 1; // Генерируем новый id
          this.employees.push({
            id: newId,
            name: this.newEmployee.name,
            salary: parseInt(this.newEmployee.salary), // Преобразуем в число
            age: parseInt(this.newEmployee.age), // Преобразуем в число
          });

          // Очищаем форму
          this.newEmployee = { name: '', salary: null, age: null };
        }
      },
    },
  };
  </script>
