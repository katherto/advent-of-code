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
      return this.puzzleData
        .split('\n')
        .map((item) => parseInt(item))
        .sort((a, b) => {
          return a - b;
        });
    },
  },
  methods: {
    twoSum(arr, sum) {
      const map = {};
      for (let i = 0; i < arr.length; i++) {
        if (map[sum - arr[i]]) {
          return [map[sum - arr[i]], i];
        }
        map[arr[i]] = i;
      }
      return -1;
    },
    threeSum(arr, sum) {
      for (let i = 0; i < arr.length; i++) {
        const indices = this.twoSum(arr, sum - arr[i]);
        if (indices !== -1 && !indices.includes(i)) {
          return [i, ...indices];
        }
      }
      return -1;
    },
    solveTwoSum() {
      const nums = this.puzzleArray;
      const solvedIndices = this.twoSum(nums, 2020);

      this.solution = `Two Sum Solution: ${
        nums[solvedIndices[0]] * nums[solvedIndices[1]]
      }`;
    },
    solveThreeSum() {
      const nums = this.puzzleArray;
      const solvedIndices = this.threeSum(nums, 2020);

      this.solution = `Three Sum Solution: ${
        nums[solvedIndices[0]] * nums[solvedIndices[1]] * nums[solvedIndices[2]]
      }`;
    },
  },
};
</script>
