<template>
  <div class="calculator">
  <div class="input" id="input">{{ show }}</div>
  <div class="buttons">
    <div class="operators">
      <div @click="add()">+</div>
      <div>-</div>
      <div>&times;</div>
      <div>&divide;</div>
    </div>
    <div class="leftPanel">
      <div class="numbers">
        <div @click="addNum(7)">7</div>
        <div @click="addNum(8)">8</div>
        <div @click="addNum(9)">9</div>
      </div>
      <div class="numbers">
        <div @click="addNum(4)">4</div>
        <div @click="addNum(5)">5</div>
        <div @click="addNum(6)">6</div>
      </div>
      <div class="numbers">
        <div @click="addNum(1)">1</div>
        <div @click="addNum(2)">2</div>
        <div @click="addNum(3)">3</div>
      </div>
      <div class="numbers">
        <div @click="addNum(0)">0</div>
        <div @click="clear()"> C </div>
        <div id="clear"> < </div>
      </div>
    </div>
    <div class="equal" id="result" @click="total()">=</div>
  </div>
</div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      numberFirst: '',
      numberSecornd: '',
      show: '',
      mode: {
        add: 0
      },
      swap: ''
    }
  },
  methods: {
    addNum (num) {
      if (this.mode.add === 1) {
        this.numberSecornd = this.numberSecornd + num.toString()
        this.show = this.numberSecornd
      } else if (this.mode.add >= 2) {
        this.numberSecornd = ''
        this.numberSecornd = this.numberSecornd + num.toString()
        this.show = this.numberSecornd
      } else {
        this.numberFirst = this.numberFirst + num.toString()
        this.show = this.numberFirst
        this.swap = this.numberFirst
      }
    },
    clear () {
      this.show = '0'
      this.numberFirst = ''
      this.numberSecornd = ''
      this.swap = ''
      this.mode.add = 0
    },
    add () {
      this.mode.add += 1
      this.show = ''
      if (this.mode.add >= 2) {
        this.show = parseInt(this.swap) + parseInt(this.numberSecornd)
        this.swap = this.show
      }
      console.log('mode ', this.mode)
      console.log('swap', this.swap)
      console.log('show', this.show)
    },
    total () {
      if (this.mode.add >= 1) {
        this.show = parseInt(this.swap) + parseInt(this.numberSecornd)
      }
    }
  },
  mounted () {
    this.show = '0'
  }
}
</script>
y
