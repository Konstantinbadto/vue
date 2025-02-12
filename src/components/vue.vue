<template>
  <div>
    <a href="page.html">page</a>
    <a href="https://www.google.com" @click.prevent>a</a>
    <!-- Убран v-if, так как clicked не используется -->
    <div>{{ name }}</div>
    <div>{{ surn }}</div>
    <p>{{ full }}</p>
    <p>{{ pr }}</p>
    <div>{{ num1 + num2 + num3 }}</div>
    <div>{{ arr[0] + arr[1] + arr[2] }}</div>
    <div>{{ obj.x + obj.y + obj.z }}</div>
    <input type="number" v-model.number="inputNumber">
    <button @click="showSquare">Показать квадрат</button>
    {{ text }}
    <button @click="change">text</button>
    <button @click="change1">text</button>
    <button @click="change2">cost</button>
    <div>Cost: {{ cost }}</div> <!-- Отображаем значение cost -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'john',
      surn: 'smit',
      text: 'page',
      href: 'page.html',
      num: 5,
      num1: 1,
      num2: 2,
      num3: 3,
      arr: [1, 2, 3],
      obj: { x: 1, y: 2, z: 3 },
      cost: 150,
      pr: 12,
      inputNumber: 0, // Число для возведения в квадрат
    };
  },
  methods: {
    change() {
      this.text = 'yyy';
    },
    change1() {
      this.text = 'vvv';
    },
    change2() {
      this.cost = 12;
    },
    showSquare() {
      //const square = this.inputNumber * this.inputNumber;
      //alert(`Квадрат числа ${this.inputNumber} равен ${square}`);
    },
  },
  computed: {
    full() {
      return this.name + ' ' + this.surn;
    },
    pr() {
      return this.cost * this.pr;
    },
  },
};
</script>
