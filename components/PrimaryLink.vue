<template>
  <div>
    <a
      class="font-bold text-blue-500 hover:text-blue-700 text-lg"
      :href="link.src"
      >{{ link.title }}</a
    >
  </div>
</template>

<script>
export default {
  props: {
    link: {
      type: Object,
      default: () => {},
    },
  },
};
</script>
