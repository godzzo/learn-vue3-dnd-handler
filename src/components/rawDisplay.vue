<template>
  <div>
    <h3>{{ title }}</h3>
    <pre class="ring-2 ring-purple-200 m-2 rounded-lg p-2">{{ value }}</pre>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    title: {
      default: '',
      type: String,
    },
    value: {
      required: true,
    },
  },
};
</script>

<style scoped>
pre {
  font-size: 10px;
  text-align: start;
}
</style>
