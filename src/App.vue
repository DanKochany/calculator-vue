<template>
  <div>
    <div class="calculator">
      <VisorContainer
        class="input-value"
        :class="changeSize ? 'to-lower-size' : ''"
      >
        {{ inputValue }}</VisorContainer
      >
      <VisorContainer
        class="input-result"
        :class="changeSize ? 'to-lower-size' : ''"
      >
        {{ inputResult }}</VisorContainer
      >
      <div class="container">
        <div
          v-for="symbol in symbols"
          :key="symbol"
        >
          <ButtonContainer @click="buttonClick(symbol)">
            {{ symbol }}
          </ButtonContainer>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import ButtonContainer from './components/ButtonContainer/ButtonContainer.vue';
import VisorContainer from './components/VisorContainer/VisorContainer.vue';

@Options({
  components: {
    ButtonContainer,
    VisorContainer,
  },
  data() {
    return {
      symbols: {
        clear: 'CE',
        answer: 'ANS',
        delete: 'DEL',
        divide: '/',
        seven: '7',
        eight: '8',
        nine: '9',
        multiply: '*',
        four: '4',
        five: '5',
        six: '6',
        minus: '-',
        one: '1',
        two: '2',
        three: '3',
        plus: '+',
        percent: '%',
        zero: '0',
        comma: ',',
        equal: '=',
      },
      changeSize: false,
      inputValue: '0',
      operationValue: 2,
      inputResult: 0,
    };
  },
  methods: {
    buttonClick(number: string) {
      if (this.inputValue == '0') {
        this.inputValue = number;
      } else if (number == '=') {
        this.inputResult = eval(this.inputValue);
      } else if (number == 'CE') {
        this.inputValue = '0';
      } else if (number == 'ANS') {
        this.inputValue = this.inputResult;
      } else {
        this.inputValue = this.inputValue + number;
      }
      this.checkSize(this.inputValue);
      this.checkSize(this.inputResult);
    },
    checkSize(value: string) {
      if (value.length >= 15) {
        this.changeSize = true;
      }
    },
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 50px auto;
  padding: 0px;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;

  .container {
    background-color: #182836;
    display: grid;
    grid-template-columns: 50px 50px 50px 50px;
    column-gap: 0px;
    border: 3px solid #000;
    border-top: 0px solid #ccc;
  }
  .input-value {
    border-top-left-radius: 20px;
    border-top-right-radius: 20px;
    font-size: 25px;
    color: bisque;
  }
  .to-lower-size {
    font-size: 15px;
  }
}
</style>
