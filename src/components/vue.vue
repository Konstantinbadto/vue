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
	}
}
    }
</script>
<template>
  <a href="page.html">page</a>
  <div>{{name}}</div>
  <div>{{surn}}</div>
  {{ num1 + num2+ num3 }}
</template>