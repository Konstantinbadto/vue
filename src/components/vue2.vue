<template>
    <div>
      <p>1</p>
      <p>2</p>
      <p :class="cssClasses">Текст с классами</p>
      <p :class="obj">text</p>
      <button @click="toggleVisibility">hide</button>
      <p :class="{ hidden: obj1.hidden }">text</p>
      <p :class="{ active: true, valid: false }">sdf</p>
      <p :class="{ active1: isActive, error: hasError }">text</p>
      <p class="styled-paragraph">текст</p>
      <p class="styled">текст</p>
      <p>{{ message }}</p>
      <input v-model="message">
      <button @click="showSquare">Показать квадрат</button>
      <button @click="toggleActive">Toggle Active</button>
      <button @click="toggleError">Toggle Error</button>
      <input type="number" v-model.number="num1" placeholder="Введите первое число">
      <input type="number" v-model.number="num2" placeholder="Введите второе число">
      <button @click="calc">Вычислить сумму</button>
      <textarea v-model="text"></textarea>

      <p>{{ text }}</p>
      <p>{{ sum }}</p>
      <button @click="processText">Обработать текст</button>
      <ul>
        <li v-for="(word, index) in words" :key="index">{{ word }}</li>
      </ul>
      <input type="checkbox" v-model="checked">
      <p v-if="checked">Этот абзац виден, если checkbox отмечен.</p>
        <input type="checkbox" v-model="knowsJavaScript"> JavaScript
        <input type="checkbox" v-model="knowsPython"> Python
        <input type="checkbox" v-model="knowsJava"> Java
        <input name="radio" type="radio" v-model="choice" value="v1">
	<input name="radio" type="radio" v-model="choice" value="v2">
	<input name="radio" type="radio" v-model="choice" value="v3">
    <p>you choosed: {{ choice }}</p>

      <p v-if="languages.length > 0">Вы знаете языки: {{ languages.join(', ') }}</p>
          <p v-if="checked">какие языки знаешь</p>
          <p>Какой ваш родной язык?</p>
      <input type="radio" value="Русский" v-model="nativeLanguage"> Русский
      <input type="radio" value="Английский" v-model="nativeLanguage"> Английский
      <input type="radio" value="Немецкий" v-model="nativeLanguage"> Немецкий
      <p>Ваш родной язык: {{ nativeLanguage }}</p>
      <select v-model="selected">
		<option>1</option>
		<option>2</option>
		<option>3</option>
	</select>
    <select v-model="selected">
		<option value="Понедельник">Понедельник</option>
      <option value="Вторник">Вторник</option>
      <option value="Среда">Среда</option>
      <option value="Четверг">Четверг</option>
      <option value="Пятница">Пятница</option>
      <option value="Суббота">Суббота</option>
      <option value="Воскресенье">Воскресенье</option>
	</select>
    <p>{{ selected }}</p>
    <input type="text" v-model="inputValue" :disabled="isDisabled">
    <button  @click="toggleDisabled">btn</button>
    <input
      type="text"
      v-model="inputText"
      @keyup.enter="addText"
      placeholder="Введите текст и нажмите Enter"
    >
    <p v-if="displayText">{{ displayText }}</p>
    <ul>
		<li v-for="(item, index) in items" :key="index">
			{{ item }}
		</li>
	</ul>
    <input v-model="newItem">
	<button @click="addItem">add</button>
    <ul>
		<li v-for="(item, index) in items" :key="index">
			{{ item }}
			<button @click="removeItem(index)">remove</button>
		</li>
	</ul>
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
      str: 'active valid',
      cssClasses: 'class1 class2 class3',
      obj: {
        done: true,
        selected: false,
      },
      obj1: {
        hidden: true,
      },
      isActive: true,
      hasError: true,
      message: 0,
      num1: 0,
      num2: 0,
      sum: 0,
      text: '',
      words: [],
      checked: true,
      knowsJavaScript: false,
      knowsPython: false,
      knowsJava: false,
      choice: '',
      nativeLanguage: '',
      selected: 'value1',
      options: ['value1', 'value2', 'value3'],
      isDisabled: true,
      inputText: '',
      displayText: '',
      newItem: '',
      items: ['a', 'b', 'c', 'd', 'e'],
      users: [
        { id: 1, name: 'name1', salary: 100, age: 30 },
        { id: 2, name: 'name2', salary: 200, age: 40 },
        { id: 3, name: 'name3', salary: 300, age: 50 },
      ],
    };
  },
  methods: {
    toggleVisibility() {
      this.obj1.hidden = !this.obj1.hidden;
    },
    toggleActive() {
      this.isActive = !this.isActive;
    },
    toggleError() {
      this.hasError = !this.hasError;
    },
    showSquare() {
      this.message = this.message * this.message;
    },
    calc() {
      this.sum = this.num1 + this.num2;
    },
    processText() {
      const trimmedText = this.text.trim();
      this.words = trimmedText.split(/\s+/);
    },
    toggleDisabled() {
      this.isDisabled = !this.isDisabled;
    },
    addText() {
      this.displayText = this.inputText;
      this.inputText = ''; // Очищаем инпут после добавления текста
    },
    addItem() {
      this.items.push(this.newItem);
    },
    removeItem(index) {
      this.items.splice(index, 1);
    },
    deleteUser(userId) {
        this.users = this.users.filter(user => user.id !== userId);
      },
  },
  computed: {
    languages() {
      const knownLanguages = [];
      if (this.knowsJavaScript) {
        knownLanguages.push('JavaScript');
      }
      if (this.knowsPython) {
        knownLanguages.push('Python');
      }
      if (this.knowsJava) {
        knownLanguages.push('Java');
      }
      return knownLanguages;
    },
  },
};
</script>

<style scoped>
p {
  color: red;
}

.class1 {
  font-weight: bold;
}

.class2 {
  text-decoration: underline;
}

.class3 {
  font-style: italic;
}

.done {
  text-align: right;
}

.selected {
  text-align: justify;
}

.hidden {
  display: none;
}

.active {
  text-decoration: line-through;
}

.valid {
  text-decoration: dashed;
}

.active1 {
  text-decoration: double;
}

.error {
  text-align: initial;
}

.styled-paragraph {
  color: green;
  background-color: yellow;
}

.styled {
  font-weight: bold;
  font-style: italic;
}
</style>
