<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-xs-4 col-xs-offset-4 dispaly">
          <h2>{{input}}</h2>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-4 col-xs-offset-4 dispaly">
          <h2>-{{dis}}%</h2>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-4 col-xs-offset-4 dispaly">
          <h2>{{discounted}}</h2>
        </div>
      </div><hr>
      <div class="row">
        <div class="col-xs-4 col-xs-offset-4 dispaly">
          <div class="row">
            <div class="col-xs-4">
                <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="setDiscount(10)"><h3>10%</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="setDiscount(20)"><h3>20%</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="setDiscount(30)"><h3>30%</h3></button><br>
            </div>
          </div><br>
          <div class="row">
            <div class="col-xs-4">
                <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="setDiscount(40)"><h3>40%</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="setDiscount(50)"><h3>50%</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="setDiscount(60)"><h3>60%</h3></button><br>
            </div>
          </div>
        </div>
      </div><br><hr>
      <div class="row">
        <div class="col-xs-4 col-xs-offset-4 box">
          <div class="row">
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(7)"><h3>7</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(8)"><h3>8</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(9)"><h3>9</h3></button>
            </div>
          </div><br>
          <div class="row">
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(4)"><h3>4</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(5)"><h3>5</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(6)"><h3>6</h3></button>
            </div>
          </div><br>
          <div class="row">
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(1)"><h3>1</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(2)"><h3>2</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(3)"><h3>3</h3></button>
            </div>
          </div><br>
          <div class="row">
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="clear"><h3>C</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="addInput(0)"><h3>0</h3></button>
            </div>
            <div class="col-xs-4">
              <button type="button" name="button" class="btn btn-outline-primary buttonAdd" @click="del"><h3><</h3></button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  components: {
  },
  data () {
    return {
      input: 0,
      dis: 0
    }
  },
  computed: {
    discounted () {
      if (isNaN(parseInt(this.input) - ((parseInt(this.input) * this.dis) / 100))) {
        return 0
      } else {
        return (parseInt(this.input) - ((parseInt(this.input) * this.dis) / 100)).toFixed(2)
      }
    }
  },
  methods: {
    setDiscount (dis) {
      this.dis = dis
    },
    addInput (input) {
      if (this.input === 0) {
        this.input = ''
        this.input = input
      } else {
        this.input += input.toString()
      }
    },
    clear () {
      this.input = 0
      this.dis = 0
    },
    del () {
      var vm = this
      var input = this.input
      input = input.split('')
      this.input = ''
      input.splice(input.length - 1, 1)
      input.forEach(i => {
        vm.input += i
      })
    }
  }
}
</script>

<style>
.dispaly {
  text-align: right;
}
.buttonAdd{
  width: 100%;
  text-align: center;
}
</style>
