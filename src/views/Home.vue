<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <input type="text" v-model="name">
    <button @click="handleClick">click me</button>
    <button @click="age++">plus age</button>
  </div>
  <br>
  <br>
  <div>
    <input type="text" v-model="search">
    <button @click="handleStop">stop watching</button>
    <p>search term - {{ search }}</p>
    <p v-for="name in matchingNames" :key="name">{{ name }}</p>
  </div>

</template>

<script>
import { ref } from '@vue/reactivity'
import { computed, watch, watchEffect } from '@vue/runtime-core'

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
    const search = ref("")
    const names = ref(['mario', 'yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach'])

    const stopWatch = watch(search,() => console.log("Watch change"))
    const stopEffect = watchEffect(()=>(console.log("WatchEffect run", search.value)))

    const matchingNames = computed(() => {
      return names.value.filter((name)=> name.includes(search.value))
    })

    const handleStop = () => {
      stopWatch()
      stopEffect()
    }
    return { names, search, matchingNames, handleStop}
  }
}
</script>
