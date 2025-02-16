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
      <button @click="toggleActive">Toggle Active</button>
      <button @click="toggleError">Toggle Error</button>
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
    },
    computed: {},
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
.styled{
    font-weight: bold;
    font-style: italic;
}
  </style>
