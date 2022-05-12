<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <input type="text" v-model="name">
    <button @click="handleClick">click me</button>
    <button @click="age++">plus age</button>
  </div>
  <div>
    <p>{{ list }}</p>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'

export default {
  name: 'Home',
  setup() {
    
    let name = ref('Kyle')
    let age = ref(20)

    const handleClick = () => {
      name.value = 'Bill'
      age.value = 30
    }

    return { name, age, handleClick}
  },
  setup() {

    let list = ['mario', 'yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach']

    return { list, }
  }
}
</script>
