<template>
    <div class="notes">
        <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index">
            <div class="note-header" :class="{full: !grid}">
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
        },
        grid: {
            type: Boolean,
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

<style lang="sass">
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
    transition: all .25s cubic-bezier(.02, .01,.47,1)
    box-shadow: 0 30px 30px rgba(0,0,0,.02)
    &.full
        width: 100%
        text-align: center
    &-header
        display: flex
        align-items: center
        justify-content: space-between
        h1
            font-size: 32px
        p
            color: #402caf
            font-size: 22px
        svg
            margin-right: 12px
            color: #999
            &.active
                color: #494ce8
            &:last-child
                margin-right: 0
        
        &.full
            justify-content: center

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