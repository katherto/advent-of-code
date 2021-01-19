<template>
  <div>
    <div class="wrapper mx-auto max-w-lg flex flex-col items-center">
      <h1 class="text-5xl font-bold">Day 1 Exercise</h1>
      <PrimaryLink
        :link="{
          src: 'https://adventofcode.com/2020/day/1/input',
          title: 'Get Puzzle Input',
        }"
      />
      <textarea
        v-model="puzzleData"
        class="mt-4 border-black border-solid border-2 text-center"
        name="puzzle_data"
        placeholder="Paste puzzle data here"
        cols="30"
        rows="10"
      ></textarea>
      <PrimaryButton
        class="mt-4"
        :button-value="'Find Two Sum Solution'"
        @click.native="solveTwoSum()"
      />
      <PrimaryButton
        class="mt-4"
        :button-value="'Find Three Sum Solution'"
        @click.native="solveThreeSum()"
      />
      <p v-if="solution" class="mt-4 text-2xl font-bold">{{ solution }}</p>
    </div>
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
    solveTwoSum() {
      const numObject = {};
      const solutionNums = [];

      this.puzzleArray.forEach((item, index) => {
        numObject[item] = index;
      });

      this.puzzleArray.every((item, index) => {
        const diff = 2020 - item;
        if (
          Object.prototype.hasOwnProperty.call(numObject, diff) &&
          numObject[diff] !== index
        ) {
          solutionNums[0] = this.puzzleArray[index];
          solutionNums[1] = this.puzzleArray[numObject[diff]];
          return false;
        }
        return true;
      });

      this.solution = `The Two Sum Solution is: ${
        solutionNums[0] * solutionNums[1]
      }`;
    },
  },
};
</script>
