<template>
    <div class="employee">
      <div v-if="!isEditing">
        <h3>{{ name }}</h3>
        <p>Зарплата: {{ salary }}</p>
        <p>Возраст: {{ age }}</p>
        <button @click="startEditing">Редактировать</button>
        <button @click="deleteEmployee">Удалить</button>
      </div>
      <div v-else>
        <label>Имя:</label>
        <input type="text" v-model="editName" />
        <label>Зарплата:</label>
        <input type="number" v-model="editSalary" />
        <label>Возраст:</label>
        <input type="number" v-model="editAge" />
        <button @click="saveChanges">Сохранить</button>
        <button @click="cancelEditing">Отмена</button>
      </div>
    </div>
  </template>

  <script>
  export default {
    props: {
      id: {
        type: Number,
        required: true,
      },
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
    },
    data() {
      return {
        isEditing: false,
        editName: this.name,
        editSalary: this.salary,
        editAge: this.age,
      };
    },
    methods: {
      startEditing() {
        this.isEditing = true;
      },
      cancelEditing() {
        this.isEditing = false;
        this.editName = this.name;
        this.editSalary = this.salary;
        this.editAge = this.age;
      },
      saveChanges() {
        this.$emit('update-employee', {
          id: this.id,
          name: this.editName,
          salary: this.editSalary,
          age: this.editAge,
        });
        this.isEditing = false;
      },
      deleteEmployee() {
        this.$emit('delete-employee', this.id);
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
