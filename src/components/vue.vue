<template>
  <div>
    <a :href="href">page</a>
    <a href="https://www.google.com" @click.prevent>a</a>
    <div>{{ name }}</div>
    <div>{{ surn }}</div>
    <p>{{ full }}</p>
    <p>{{ calculatedPr }}</p>
    <div>{{ num1 + num2 + num3 }}</div>
    <div>{{ arr[0] + arr[1] + arr[2] }}</div>
    <div>{{ obj.x + obj.y + obj.z }}</div>
    <input type="number" v-model.number="inputNumber">
    <button @click="showSquare">Показать квадрат</button>
    <div>{{ squareResult }}</div>
    <div>{{ text }}</div>
    <button @click="changeTextToYyy">Change text to yyy</button>
    <button @click="changeTextToVvv">Change text to vvv</button>
    <button @click="changeCost">Change cost</button>
    <div>Cost: {{ cost }}</div>
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
    <p v-for="(elem, index) in items" >{{ elem }}</p>
    <p v-for="(elem, index) in arr1" >{{ elem }}</p>
    <p v-for="(elem, index) in items" >{{ elem**2 }}</p>
    <ul>
      <li v-for="(elem, index) in items" >{{ elem }}</li>
    </ul>
    <p v-for="(value, key, index) in obj1" >
      {{ key }} - {{ value }} - {{ index + 1 }}
    </p>
    <ul>
      <li v-for="(item, index) in items" >{{ item }}</li>
    </ul>
    <div v-for="(item, index) in items" >
      <p>{{ item }}</p>
      <p class="divider"></p>
    </div>
    <ul>
      <li v-for="(item, index) in items" >
        {{ item }}
      </li>
      <li class="divider"></li>
    </ul>
    <ul>
      <li v-for="(link, index) in hrefs" >
        <a :href="link.href">{{ link.text }}</a>
      </li>
    </ul>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Price</th>
          <th>Quantity</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in products" >
          <td>{{ item.name }}</td>
          <td>{{ item.price }}</td>
          <td>{{ item.quantity }}</td>
        </tr>
      </tbody>
    </table>
    <p v-for="num in 30" :key="num">
      {{ num }}
    </p>
      <p v-for="(elem, index) in arr2"  v-if="elem >= 0">
        {{ elem }}
      </p>
       <p v-for="product in products1" :key="products1.id">
      {{ products1.name }}
	</p>
  <p v-for="elem in arr1">
		{{ elem }}
	</p>
	<button @click="add">add</button>
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
      squareResult:0,
      visible: false,
      v: true,
      e: true,
      isAdmin: true,
      day: 7,
      age: 25,
      isAuth: true,
      items: [1, 2, 3, 4, 5],
      arr1: ['a', 'b', 'c'],
      obj1: {
        user1: '100$',
        user2: '200$',
        user3: '300$',
      },
      hrefs: [
        { href: '1.html', text: 'text1' },
        { href: '2.html', text: 'text2' },
        { href: '3.html', text: 'text3' },
      ],
      products: [
        { name: 'product1', price: 100, quantity: 5 },
        { name: 'product2', price: 200, quantity: 4 },
        { name: 'product3', price: 300, quantity: 3 },
      ],
      arr2: [1, -2, 3, -4, 5],
      products1: [
			{
				id: 1,
				name: 'product1',
			},
			{
				id: 2,
				name: 'product2',
			},
			{
				id: 3,
				name: 'product3',
			},
		]
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
      this.squareResult = this.inputNumber * this.inputNumber;
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
    togglea() {
      this.isAuth = !this.isAuth;
    },
  },
  add: function() {
		this.arr.push('xxx');
	},
  computed: {
    full() {
      return this.name + ' ' + this.surn;
    },
    calculatedPr() {
      return this.cost * this.pr;
    },
  },
};
</script>
