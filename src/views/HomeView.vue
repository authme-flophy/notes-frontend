<script setup>
 
  import { ref, watch, onMounted } from 'vue';
  import axios from 'axios';
  import NoteItem from '../components/NoteItem.vue';
  import NotesCreate from '../components/NotesCreate.vue';

  const noteList = ref([])

  watch(noteList, () => {
    setNoteListLocalStorage()
  }, {
    deep: true,
  })

  const fetchNoteList = () => {
    const savedNoteList = JSON.parse(localStorage.getItem("noteList"))
    if (savedNoteList) {
      console.log(savedNoteList);
      noteList.value = savedNoteList
    }
  }

  onMounted(() => {
    fetchNoteList()
    axios
      .get('http://localhost:8000/api/notes/')
      .then((response) => {
        noteList.value = response.data
      })
      .catch((err) => {
        console.error(err)
      })


  })

  const setNoteListLocalStorage = () => {
    localStorage.setItem("noteList", JSON.stringify(noteList.value))
  }

  const createNote = (note) => {
    axios
      .post('http://localhost:8000/api/notes/', {
        title: note.value.title,
        content: note.value.content,
      })
      .then(response => console.log(response.status))
    noteList.value.push({
      title: note.value.title,
      content: note.value.content
    })
  }

</script>

<template>
  <NotesCreate @create-note="createNote"/>
  <ul class="note-list" v-if="noteList.length > 0">
    <NoteItem v-for="(note, index) in noteList" :note="note" :key="index"/>
  </ul>
  <p class="notes-empty-message" v-else>You have no notes</p>
</template>

<style lang="scss">
  .note-list {
    margin-top: 2rem;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
  }
</style>
