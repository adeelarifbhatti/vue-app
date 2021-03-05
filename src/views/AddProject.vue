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
        margin: .2rem auto;
         background-color: #bbdaf3;
        border-radius: .5rem;
        padding: 3rem;
        clip-path: polygon(0% 10%, 100% 0, 100% 100%, 0% 93%);
    }
.input {
    font-size: 1.1rem;
    font-family: inherit;
    padding: .5rem .2rem;
    border-radius: .5rem;
    background: rgba(168, 145, 145, 0.192);
    background-color: rbga(rgb(55, 99, 105), .5);
    border: none;
    border: .2rem solid rgba(46, 92, 122, 0.747);
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