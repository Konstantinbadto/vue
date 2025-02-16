<template>
    <div>
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Имя</th>
            <th>Зарплата</th>
            <th>Возраст</th>
            <th>Действия</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.salary }}</td>
            <td>{{ user.age }}</td>
            <td>
              <a href="#" @click.prevent="deleteUser(user.id)">Удалить</a>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>

  <script>
  export default {
    data() {
      return {
        users: [
          { id: 1, name: 'name1', salary: 100, age: 30 },
          { id: 2, name: 'name2', salary: 200, age: 40 },
          { id: 3, name: 'name3', salary: 300, age: 50 },
        ],
      };
    },
    methods: {
      deleteUser(userId) {
        this.users = this.users.filter(user => user.id !== userId);
      },
    },
  };
  </script>

  <style scoped>
  table {
    width: 100%;
    border-collapse: collapse;
  }

  th,
  td {
    border: 1px solid black;
    padding: 8px;
    text-align: left;
  }

  th {
    background-color: #f2f2f2;
  }
  </style>
