<template>
  <div class="project" :class="{complete: project.complete}">
      <div class="actions" >
          <h3 @click="showDetailAction()"> {{project.title}} </h3>

        <div class="details" v-if="showDetails">
           <p> {{project.details}} </p>
        </div>
            <div class="icons">
                <span @click="doneProject" class="material-icons">done_all</span> 
                <span class="material-icons">edit</span> 
                <span @click="deleteProject" class="material-icons">delete</span> 
            </div>

      </div>
  </div>
</template>

<script>
export default {
    props: ['project'],
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
    margin: 2rem auto;
    background: rgb(216, 213, 213);
    padding: 1rem 2rem;
    border-radius: .4rem;
    box-shadow: .8rem .5rem 1rem rgba(0, 0, 0, .5);
    border-left: .8rem solid rgba(243, 63, 63, 0.384);
}
.complete {
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


</style>