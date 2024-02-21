<template lang="">
    <div class="container">
        <div class="row">
            
                <div class="card col-4 mx-2 mb-4" v-for="project in projects" style="width: 25rem;">
            <div class="card-body">
            <h5 class="card-title">
                {{ project.nome }}
            </h5>
               <p class="card-text">
                {{project.descrizione}}
            </p>
             <p>
                   {{project.linguaggi_usati}}
             </p>
             <p>
                {{project.type.tipo}}
             </p>
             <p class="text-primary">{{project.repo_url}}</p>
    </div>
            </div>
    </div>
</div>

</template>
<script>
import axios from 'axios';

export default {
    name: 'AppMain',

    data() {
        return {
            projects:[],
        }
    },

    methods:{
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                
                }
            })
            .then((response)=> {
                console.log(response.data.results.data);
                this.projects = response.data.results.data;
            })
            .catch(function (error) {
                console.warn(error);
            })
            
        }
    },

    created() {
        this.getProjects();
    },
    
}

</script>
<style lang="">
    
</style>