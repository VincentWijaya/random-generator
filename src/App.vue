<template>
  <div id="app">
    Min:<br>
    <input type="text" v-model="from" placeholder="1"><br><br>
    Max:<br>
    <input type="text" v-model="to" placeholder="100"><br><br>
    <button @click="randomize">{{ button }}</button>

    <h1>{{ number }}</h1>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      number: 0,
      button: 'Start',
      from: 1,
      to: 100
    }
  },
  methods: {
    randomize () {
      if (this.button === 'Start' && !this.randomNumber) {
        this.randomNumber = setInterval(() => {
          this.number = Math.floor((Math.random() * this.to) + this.from)
        }, 100)
        this.button = 'Stop'
        this.number = this.randomNumber
      } else {
        this.button = 'Start'
        clearInterval(this.randomNumber)
        delete this.randomNumber
      }
    }
  }
}
</script>
