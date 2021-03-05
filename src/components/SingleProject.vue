<template>
    <div id="projects" class="project" :class="{complete: project.complete}">
        <div class="actions" >
            <h3 @click="showDetailAction()"> 
                {{project.title}} 
            </h3>
            <div class="icons">
                <router-link :to="{name: 'EditProject', params: {id: project.id}}">
                    <span  class="material-icons">edit</span> 
                </router-link>
                <span @click="doneProject" class="material-icons">done_all</span> 
                <span @click="deleteProject" class="material-icons">delete</span> 
            </div>     
        </div>      
    </div>

    <div class="details" v-if="showDetails">
                <div class="project-details">
                    <h3> Project Details </h3>
                    {{project.details}}
                    <button class="btn-close" @click="showDetailAction">close</button> 
                </div>

    </div>                        


</template>

<script>
export default {
    props: ['project'],
    emits: ['complete', 'delete'],
    data() {
        return {
             showDetails: false,
             uri: 'http://mol.uio.no:3000/projects/'+this.project.id
        }
    },
    methods: {
        showDetailAction(){
            this.showDetails=!this.showDetails;
            console.log("Showing Details");
        },
        doneProject() {
            fetch(this.uri, {
                method: 'PATCH',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({complete: !this.project.complete})
                }).then(() => {
                    this.$emit('complete',this.project.id)
                }).catch((err) => console.log(err));
        },

        deleteProject() {
            fetch(this.uri, {method: 'DELETE'})
                .then(()=> this.$emit('delete',this.project.id))
                .then(console.log("Deleting Project"))
                    .catch(err => console.log(err));  
        }    
    }

}
</script>

<style>
.project {
    margin-right: 10rem;
    margin-left: 10rem;
    margin-bottom: 2rem;
    background: rgba(195, 219, 126, 0.5);
    padding: .5rem .5rem .5rem .5rem;
    border-radius: .4rem;
    box-shadow: .8rem .5rem 1rem rgba(0, 0, 0, .5);
    border-left: .8rem solid rgba(243, 63, 63, 0.384);
}
.details{
    height: 100vh;
    width: 100%;
    background: rgba(65, 171, 197, 0.5);
    position: fixed;
    top:0;
    left:0;
}
.project-details{
    position: absolute;
    font-size: 1rem;
    overflow: hidden;
    top:40%;
    left:50%;
    padding: 3rem;
    width: 70%;
    height: 70%;
    background-color: rgba(21, 72, 211, 0.37);
    box-shadow: 0 2rem 4rem rgba(rgb(70, 55, 57),.2);
    border-radius: 3px;
    text-align: center;
    opacity: 1;
    transform: translate(-50%,-50%);
}

.project.complete {
        border-left: .8rem solid rgba(140, 233, 52, 0.986);

}
h3 {
    cursor: pointer;
}
.actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.material-icons {
    font-size: 1.4rem;
    margin-left: 1rem;
    color: rgb(148, 154, 155);
    cursor: pointer;
}
.material-icons:hover {
    color: rgb(121, 126, 126);
}
.btn-close {
   position: absolute;
   background-color: rgb(165, 165, 192);
   top: 1rem;
   right: 1rem;
 border: .1rem solid black;
}


</style>