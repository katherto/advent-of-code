<template>
  <div>
    <input
      type="button"
      :value="buttonValue"
      class="py-2 px-3 rounded-3xl font-bold text-white bg-blue-500 hover:bg-blue-700 cursor-pointer outline-none"
    />
  </div>
</template>

<script>
export default {
  props: {
    buttonValue: {
      type: String,
      default: '',
    },
  },
};
</script>
