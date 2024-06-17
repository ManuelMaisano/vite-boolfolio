<template>
    <div>
        <h1>Progetti</h1>
        <p>Questi sono i progetti:</p>
        <div class="row">
            <div class="col-md-4" v-for="project in projects" :key="project.id">
                <CardComponent :project="project" />
            </div>
        </div>
    </div>
</template>

<script>


import axios from 'axios';
import CardComponent from '../components/CardComponent.vue';



export default {
    name: 'Projects',
    components: {
        CardComponent
    },
    data() {
        return {
            projects: []
        };
    },
    created() {
        axios.get('http://localhost:8000/api/projects')
            .then(response => {
                this.projects = response.data;
                console.log(response.data);
            })
            .catch(error => {
                console.error('Error fetching projects:', error);
            });
    }
};
</script>