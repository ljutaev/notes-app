<template>
    <div class="new-note">
        <label>Title</label>
        <input v-model="note.title" type="text">
        <label>Description</label>
        <textarea v-model="note.description"></textarea>
        <button class="btn btnPrimary" @click="addNote">New note</button>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
    methods: {
        addNote () {
            this.$emit('addNote', this.note)
        }
    }
}
</script>

<style lang="sass" scoped>
    .new-note
        text-align: center
        textarea
            margin-bottom: 18px
</style>