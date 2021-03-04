<template>
  <form class= "form" @submit.prevent="handleSubmit">
      <label class="label"> Title:</label>
      <input class= "input" type="text" v-model="title" required>
      <label class="label">Details:</label>
      <textarea class="input" v-model="details" requried></textarea>
      <button class="btn"> Add Project </button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            details: ''
        }
    },
    methods: {
        handleSubmit() {
            let project = {
                title: this.title,
                details: this.details,
                complete: false
            }
            fetch('http://mol.uio.no:3000/projects',{
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(project)
            })
            .then(()=> console.log("Adeel Testing",project))
            .then(()=> {
                this.$router.push({name: 'Home'})
            })
            .catch((err) => console.log(err))
        }

        }
    }
</script>

<style>
.btn {
    text-transform: uppercase;
    text-decoration: none;
    margin-top: 2rem;
    padding: .5rem 1rem;
    display: inline-block;
    border-radius: .9rem;
    transition: all .3s;
    background-color: rgba(96, 224, 84, 0.411);
    color: rgb(24, 22, 19);
    }
.form { 
        margin-top: 5rem;
        background: rgba(192, 174, 174, 0.288);
        border-radius: 1rem;
        padding: 9rem;
    }
.input {
    font-size: 1.1rem;
    font-family: inherit;
    padding: .5rem .2rem;
    border-radius: .5rem;
    background: rgba(168, 145, 145, 0.192);
    background-color: rbga(rgb(170, 131, 131), .5);
    border: none;
    border: .2rem solid rgba(194, 184, 184, 0.589);
    width: 80%;
    display: block;
}
.label {
    font-size: 1.2rem;
    font-weight: 10;
    margin-left: .2rem;
    margin-top: .7rem;
    display: block;    
}


    

</style>