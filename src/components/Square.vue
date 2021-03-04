<template>
    <!-- eslint-disable-next-line max-len -->
    <div ref="square" class="square" v-on:click="emitNumber">
      <p ref="displayText">{{ displayText }}</p>
    </div>
</template>

<script>
export default {
  name: 'Square',
  props: ['number'],
  data() {
    return {
      displayText: '',
    };
  },
  methods: {
    emitNumber() {
      this.$emit('onclick', this.number);
    },
    setDisplayText(text) {
      this.displayText = text;
    },
    colorSquareIfClicked(i) {
      if (i === this.number) {
        this.$refs.square.style.backgroundColor = 'red';
      } else {
        this.$refs.square.style.backgroundColor = 'blue';
      }
    },
  },
};
</script>

<style scoped>
  .square {
      width: 300px;
      height: 300px;
      background-color: blue;
  }

  p {
    font-size: 6em;
    display: flex;
    color: white;
    align-items: center;
    justify-content: space-around;
  }
</style>
