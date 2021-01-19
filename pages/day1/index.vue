<template>
  <div>
    <h1>Day 1 Exercise</h1>
    <textarea
      id="puzzleData"
      v-model="puzzleData"
      name="puzzle_data"
      cols="30"
      rows="10"
    ></textarea>
    <input type="button" value="Find Solution" @click="solve()" />
    <p v-if="solution">The solution is: {{ solution }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      puzzleData: '',
      solution: null,
    };
  },
  computed: {
    puzzleArray() {
      return this.puzzleData.split('\n').map((item) => parseInt(item));
    },
  },
  methods: {
    solve() {
      const numObject = {};
      const solutionNums = [];

      this.puzzleArray.forEach((item, index) => {
        numObject[item] = index;
      });

      for (let i = 0; i < this.puzzleArray.length; i++) {
        const diff = 2020 - this.puzzleArray[i];
        if (
          Object.prototype.hasOwnProperty.call(numObject, diff) &&
          numObject[diff] !== i
        ) {
          solutionNums[0] = this.puzzleArray[i];
          solutionNums[1] = this.puzzleArray[numObject[diff]];
        }
      }

      this.solution = solutionNums[0] * solutionNums[1];
    },
  },
};
</script>
