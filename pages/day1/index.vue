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
  </div>
</template>

<script>
export default {
  data() {
    return {
      puzzleData: '',
    };
  },
  computed: {
    puzzleArray() {
      return this.puzzleData.split('\n').map((item) => parseInt(item));
    },
  },
  methods: {
    solve() {},
  },
};
</script>
