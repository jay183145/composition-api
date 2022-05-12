<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'

export default {
  name: 'Home',
  setup() {

    const p = ref(null)
    let name = 'mario'
    let age = 30

    const handleClick = (e) => {
      console.log(p, p.value)
      p.value.classList.add('DoM')
      p.value.textContent ="I Made it!"
    }

    return { name, age, handleClick, p }
  },
}
</script>
