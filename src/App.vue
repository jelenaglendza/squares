<template>
  <div id="app">
    <main>
      <!-- eslint-disable-next-line max-len -->
      <square
        :ref="`square`+i"
        v-for="i in this.numbers"
        :key="i" :number="i"
        @onclick="onClick"
      ></square>
    </main>
  </div>
</template>

<script>
import Square from './components/Square.vue';

export default {
  name: 'App',
  components: {
    Square,
  },
  data() {
    return {
      numbers: [1, 2, 3],
    };
  },
  methods: {
    onClick(i) {
      this.printNumber(i);
      this.colorClickedSquare(i);
    },
    printNumber(i) {
      this.$refs.square2.setDisplayText(i);
    },
    colorClickedSquare(i) {
      this.numbers
          .map((n) => this.$refs['square' + n])
          .forEach((square) => square.colorSquareIfClicked(i));
    },
  },
};
</script>

<style>

  body, html {
    height: 100vh;
    margin: 0px;
  }

  #app {
    width: 100%;
    height: 100%;
    background-color: yellow;
    display: flex;
    align-items: center;
  }

  main {
    width: 100%;
    display: flex;
    justify-content: space-around;

  }
</style>
