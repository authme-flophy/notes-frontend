<template>
  <li>
    <h1>{{ note.title }}</h1>
    <p>{{ note.content }}</p>
    <div class="note-buttons">
      <Icon icon="solar:pen-outline" color="#41b883" width="20" class="edit-button"/>
    </div>
  </li>
</template>

<script setup>
  import { Icon } from '@iconify/vue';

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

  .edit-button {
    cursor: pointer;
    transition: all .2s ease-in-out;

    &:hover {
      transform: rotateY(180deg);
    }

  }

  .note-buttons {
    margin-top: 1rem;
    padding-top: .5rem;
    border-top: 1px solid #34495E;
  }

</style>