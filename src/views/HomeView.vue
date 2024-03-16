<template>
  <div>
    <h2>Notes</h2>
    <input v-model="newNote" />&nbsp;
    <button @click="addNewNote">AddNotes</button>
    <p v-for="note in notes" :key="note.id">
      <b>* {{ note.description }}</b>
    </p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      notes: [],
      newNote: ''
    };
  },
  mounted() {
    // Wywołanie metody do pobierania notatek po zamontowaniu komponentu
    this.getNotes();
  },
  methods: {
    async getNotes() {
      try {
        const response = await axios.get('http://localhost:5024/api/notes/GetNotes');
        this.notes = response.data;
      } catch (error) {
        console.error('Błąd podczas pobierania notatek:', error);
      }
    },
    async addNewNote() {
      try {
        await axios.post('http://localhost:5024/api/notes/AddNotes', { newNotes: this.newNote });
        // Aktualizuj listę notatek po dodaniu nowej notatki
        await this.getNotes();
        // Wyczyść pole tekstowe po dodaniu notatki
        this.newNote = '';
      } catch (error) {
        console.error('Błąd podczas dodawania notatki:', error);
      }
    }
  }
};
</script>
