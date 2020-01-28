<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>
          <message 
            v-if="message" 
            :message="message" 
          />
          <newNote 
            :note="note"
            @addNote="addNote"
          />
          <notes 
            :notes="notes"
            @remove="removeNote"
          />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import message from '@/components/Message'
import notes from '@/components/Notes'
import newNote from '@/components/NewNote'
export default {
  components: {
    message,
    newNote,
    notes
  },
  data () {
    return {
      title: 'Notes App',
      message: null,
      note: {
        title: '',
        description: ''
      },
      notes: [
        {
          title: 'First Note',
          description: 'Description for first note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Second Note',
          description: 'Description for second note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Third Note',
          description: 'Description for third note',
          date: new Date(Date.now()).toLocaleString()
        },
      ]
    }
  },
  methods: {
    addNote () {
      let {title, description} = this.note

      if( title == '') {
        this.message = 'title can`t be blank'
        return false
      }

      this.notes.push({
        title,
        description,
        date: new Date(Date.now()).toLocaleString()
      })

      this.note.title = ''
      this.note.description = ''
      this.message = null
      console.log(this.note)
    },
    removeNote(index) {
      this.notes.splice(index, 1)
    }
  }  
}
</script>

<style>

</style>
