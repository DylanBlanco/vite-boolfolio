<script>
// import axios
import axios from 'axios';

export default {
    data() {
        return {
          projects: [],
        }
    },
    // created() {
    //   axios
    //     //   .get('http://localhost/phpMyAdmin5/index.php?route=/database/structure&server=1&db=classe130_boolfolio')
    //       .get('http://localhost/phpMyAdmin5/index.php?route=/sql&db=classe130_boolfolio&table')
    //       .then((res) => {
    //           console.log('oggetto creato da axios',res);
    //           console.log('dati che ci ha risposto il server', res.data.data);

    //           // salva dati
    //           this.projects = res.data;
    //       });
    // },
    async mounted() {
        try {
        const response = await axios.get('http://localhost:8000/api/projects');
        this.projects = response.data;
        } 
        catch (error) {
        console.error('Errore nel recupero dei progetti:', error);
        }
    },
    methods: {
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