<template>
    <form @submit.prevent="handleSubmit" method="post">
        <label for="">Title:</label>
        <input type="text" required v-model="title">
        <label for="">Details:</label>
        <textarea required v-model="details"></textarea>
        <button type="button">Add</button>
    </form>
</template>

<script>
export default {
    name: 'AddProjectView',
    // Your component options go here
    data() {
        return {
            title: '',
            details: '',
        }
    },
    methods: {
        handleSubmit() {
            console.log(this.title, this.details)
    }
    }
}
</script>

<style scoped>
/* Your component styles go here */
</style>
