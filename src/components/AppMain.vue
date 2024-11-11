<script>
// import axios
import axios from 'axios';

export default {
    data() {
        return {
          projects: [],
        }
    },
    // async mounted() {
    //     try {
    //     const response = await axios.get('http://localhost:8000/api/projects');
    //     this.projects = response.data;
    //     } 
    //     catch (error) {
    //     console.error('Errore nel recupero dei progetti:', error);
    //     }
    // },
    mounted() {
        this.getProjects();
    },
    methods: {
        getProjects () {
            axios
                .get('http://localhost:8000/api/projects')
                .then((res) => {
                    console.log(res.data);
                    this.projects = res.data;
                });
        }
    }
}
</script>

<template>
    <main>
        <div class="row p-5">
            <div  v-for="(project, i) in projects" :key="i" class="card m-3" style="max-width: 540px;">
                <div class="row g-0">
                    <div class="col-md-4">
                        <img src="..." class="img-fluid rounded-start" alt="...">
                    </div>
                    <div class="col-md-8">
                        <div class="card-body">
                            <h5 class="card-title">{{ project.title }}</h5>
                            <p class="card-text">{{ project.author }}</p>
                            <p class="card-text">{{ project.description }}</p>
                            <p class="card-text"><small class="text-body-secondary">{{ project.date_create }}</small></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>