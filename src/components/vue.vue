<template>
  <div>
    <a href="page.html">page</a>
    <a href="https://www.google.com" @click.prevent>a</a>
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
    <button @click="changeTextToYyy">Change text to yyy</button>
    <button @click="changeTextToVvv">Change text to vvv</button>
    <button @click="changeCost">Change cost</button>
    <div>Cost: {{ cost }}</div>
    <!-- Упрощенное управление видимостью абзацев -->
    <button @click="toggleVisible">
      Toggle Visibility {{ visible ? 'hide' : 'show' }}
    </button>
    <p v-if="visible">Text when 'visible' is true.</p>

    <button @click="toggleV">
      Toggle V {{ v ? 'hide' : 'show' }}
    </button>
    <p v-if="v">Textff</p>

    <button @click="toggleE">
      Toggle E {{ e ? 'hide' : 'show' }}
    </button>
    <p v-if="e">Textdd</p>
    <p v-if="isAdmin">+++</p>
    <p v-else>---</p>

    <p v-if="day === 1">пон</p>
	  <p v-if="day === 2">втор</p>
	  <p v-if="day === 3">сре</p>
	  <p v-if="day === 4">чет</p>
	  <p v-if="day === 5">пят</p>
	  <p v-if="day === 6">суб</p>
	  <p v-if="day === 7">вос</p>

    <p v-if="age <= 18">подросток</p>
    <p v-else-if="age <= 25">молодой</p>
    <p v-else>дед</p>
    <button @click="togglea">
       {{ isAuth ? 'hide' : 'show' }}
    </button>
    <div v-if="isAuth">
		<p>+++</p>
		<p>+++</p>
		<p>+++</p>
	</div>
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
      inputNumber: 0,
      visible: false,
      v: true,
      e: true,
      isAdmin: true,
      day: 7,
      age: 25,
      isAuth: true,
    };
  },
  methods: {
    changeTextToYyy() {
      this.text = 'yyy';
    },
    changeTextToVvv() {
      this.text = 'vvv';
    },
    changeCost() {
      this.cost = 12;
    },
    showSquare() {
      const s = this.inputNumber * this.inputNumber;
      alert(`Квадрат числа ${this.inputNumber} равен ${s}`);
    },
    toggleVisible() {
      this.visible = !this.visible;
    },
    toggleV() {
      this.v = !this.v;
    },
    toggleE() {
      this.e = !this.e;
    },
    togglea(){
      this.isAuth = !this.isAuth
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
