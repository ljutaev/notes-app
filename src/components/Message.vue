<template>
    <div class="message">
        <p>{{ message }}</p>
    </div>    
</template>

<script>
export default {
    props: {
        message: {
            type: String,
            required: true
        }
    }
}
</script>

<style lang="sass" scoped>
    .message
        text-align: center
        color: #ba3838
        padding: 25px
</style>