<template>
    <div class="project">
        <div class="actions">
            <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
            <div class="icons">
                <i class="fa-solid fa-check fa-xl"></i>
            </div>
        </div>
        <div class="details" v-if="showDetails">
            <p>{{ project.details }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SingleProject',
    // Your component's properties, methods, etc. go here
    props: ['project'],
    data () {
        return {
            showDetails: false,
        }
    }
}
</script>

<style scoped>
/* Your component's styles go here */
    .project {
        background: #fff;
        border-radius: 5px;
        box-shadow: 0 2px 4px rgba(0,0,0,0.18), 0 2px 4px rgba(0,0,0,0.24);
        margin: 20px auto;
        padding: 10px 20px;
        border-left: 4px solid #e90074;
    }
    h3 {
        cursor: pointer;
    }

</style>
