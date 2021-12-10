<template>
  <section v-if="hasFruits">
    <h2>Fruits</h2>
    <ul>
      <li v-for="fruits in fruits" :key="fruits">{{ fruits }}</li>
    </ul>
  </section>

  <section>
    <h2>Reverse Fruits</h2>
    <ul>
      <li v-for="fruit in reverseFruits" :key="fruit">{{ fruit }}</li>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      fruits: ['Banana', 'Apple', 'Cherry']
    }
  },

  computed: {
    hasFruits() {
      return this.fruits.length > 0
    },

    reverseFruits() {
      return this.fruits.map(fruit => {
        //'Apple' => ['A', 'p', 'p', 'l', 'e'] => ['e', 'l', 'p', 'p', 'A'] => 'elppA'
        return fruit.split('').reverse().join('')
      })
    }
  }
}
</script>