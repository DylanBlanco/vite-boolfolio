<script>
// import axios
import axios from 'axios';

export default {
    data() {
        return {
          projects: [],
        }
    },
    created() {
      axios
          .get('http://localhost/phpMyAdmin5/index.php?route=/sql&db=classe130_boolfolio&table=projects&pos=0')
          .then((res) => {
              console.log('oggetto creato da axios',res);
              console.log('dati che ci ha risposto il server', res.data);

              // salva dati
              this.projects = res.data.data;
          });
    },
    methods: {
    }
}
</script>

<template>
    <main>
        <div class="card mb-3" style="max-width: 540px;">
            <div class="row g-0">
                <div class="col-md-4">
                    <img src="..." class="img-fluid rounded-start" alt="...">
                </div>
                <div class="col-md-8">
                    <div class="card-body">
                        <h5 class="card-title">Card title</h5>
                        <p class="card-text">This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
                        <p class="card-text"><small class="text-body-secondary">Last updated 3 mins ago</small></p>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>