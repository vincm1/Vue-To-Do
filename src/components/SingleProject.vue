<template>
    <div class="project" :class="{ complete: project.complete }">
        <div class="actions">
            <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
            <div class="icons">
                <i @click="toggleComplete" class="fa-solid fa-check" :class="{ complete: project.complete }"></i>
                <i class="fa-solid fa-pen"></i>
                <i @click="deleteProject" class="fa-solid fa-trash"></i>
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
            uri: 'http://localhost:3000/projects/' + this.project.id, 
        }
    },
    methods: {
        deleteProject() {
            fetch(this.uri, {method: 'DELETE'})
                .then(() => this.$emit('delete', this.project.id))
                .catch(err => console.log(err))
        },
        toggleComplete() {
            fetch(this.uri, {
                method: 'PATCH',
                headers: { 'Content-Type': 'application/json'},
                body: JSON.stringify({complete: !this.project.complete}),
            }).then(() => {
                this.$emit('complete', this.project.id)
            }).catch((err) => console.log(err))

        }
    },
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
    .actions {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 5px 5px;
    }

    .project.complete {
        border-left: 4px solid #00c853;
    }

    .icons {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .fa-solid {
        margin: 0 7px;
        cursor: pointer;
    }

    .fa-solid.complete {
        color: #00c853;
    }

    .fa-solid:hover {
        color: #e90074;
    }

</style>
