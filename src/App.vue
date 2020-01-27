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

          <div class="notes">
            <div class="note" v-for="(note, index) in notes" :key="index">
              <div class="note-header">
                <p>{{ note.title }}</p>
              </div>
              <div class="note-body">
                <p>{{ note.description }}</p>
                <span>{{ note.date }}</span>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import message from '@/components/Message'
import newNote from '@/components/NewNote'
export default {
  components: {
    message,
    newNote
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
    }
  }  
}
</script>

<style>

</style>
