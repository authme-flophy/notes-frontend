<template>
  <div class="create-form">
    <input type="text" name="title" id="title" placeholder="Title" v-model="noteState.title">
    <textarea name="content" id="content" cols="30" rows="3" placeholder="content" v-model="noteState.content"></textarea>
    <button class="submit-button" @click="createNote()">Create</button>
  </div>
</template>

<script setup>
  import {ref, defineEmits} from 'vue'

  const emit = defineEmits(['create-note'])

  const noteState = ref({
    title: "",
    content: ""
  })

  const createNote = () => {
    if (noteState.value.content !== "") {
      emit('create-note', noteState)
      noteState.value.title = ""
      noteState.value.content = ""
    } else {
      alert("Content cannot be blank")
    }

  }

</script>

<style lang="scss" scoped>
  .create-form {
    width: 400px;
    display: flex;
    flex-direction: column;
  }

  #title {
    margin: .5rem 0;
    padding: .5rem .5rem;
    font-size: 20px;
    border: 1px solid #34495E;
    color: #41B883;
    border-radius: 10px;
    font-weight: bold;

    &:focus {
      outline: none;
    }

    &::placeholder {
      color: hsl(153, 48%, 60%);
    }

  }

  #content {
    margin: .5rem 0;
    padding: .5rem .5rem;
    font-size: 16px;
    border: 1px solid #34495E;
    border-radius: 10px;

    &:focus {
      outline: none;
    }

  }

  .submit-button {
    background-color: #41B883;
    border: #41B883;
    color: white;
    font-size: 18px;
    text-transform: uppercase;
    padding: .5rem 0;
    border-radius: 10px;
    cursor: pointer;
    transition: all .2s ease-in-out;

    &:hover {
      transform: scale(1.02);
    }

  }



</style>