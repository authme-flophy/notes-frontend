<template>
  <li>
    <h1>{{ note.title }}</h1>
    <p>{{ note.content }}</p>
  </li>
</template>

<script setup>
  const props = defineProps({
    note: {
      type: Object,
      required: true,
    }
  })
</script>

<style lang="scss" scoped>
  li {
    list-style-type: none;
    border: 2px solid #34495E;
    margin: .5rem;
    padding: .5rem .5rem;
    border-radius: 10px;
    min-width: 300px;

    h1 {
      color: #41B883;
    }

  }
</style>