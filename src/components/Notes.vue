<template>
    <div class="notes">
        <div class="note" v-for="(note, index) in notes" :key="index">
            <div class="note-header">
                <p>{{ note.title }}</p>
                <p class="close" @click="removeNote(index)">x</p>
            </div>
            <div class="note-body">
                <p>{{ note.description }}</p>
                <span>{{ note.date }}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            required: true
        }
    },
    methods: {
        removeNote( index ) {
            console.log(`Note id - ${index} removed`)
            this.$emit('remove', index)
        }
    }
}
</script>

<style lang="sass" scoped>
.notes
    display: flex
    align-items: center
    justify-content: space-between
    flex-wrap: wrap
    padding: 48px 0

.note
    width: 48%
    padding: 10px 40px
    margin-bottom: 20px
    background: #fff
    position: relative
    &-header
        p
            color: #402caf
            font-size: 22px
    &-body
        p 
            margin: 20px
        span
            color: #999
            font-size: 14px
.close
    cursor: pointer
    position: absolute
    top: 0
    right: 10px
</style>