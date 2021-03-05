<template>
  <h1>
      Edit Project
  </h1>
    <form class= "form" @submit.prevent="handleEdit">
      <label class="label"> Title:</label>
      <input class= "input" type="text" v-model="title" required>
      <label class="label">Details:</label>
      <textarea class="input" v-model="details" requried></textarea>
      <button class="btn"> Update Project </button>
  </form>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            title: '',
            details:'',
            uri: process.env.VUE_APP_URL+'/'+this.id
        }
    },
    methods: {
        handleEdit() { 
            fetch(this.uri,{
                method: 'PATCH',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({title: this.title, details: this.details})
            })
            .then(()=> console.log("Adeel Testing",this.title, " And ", this.details))
            .then(()=> {
                this.$router.push({name: 'Home'})
            })
            .catch((err) => console.log(err))
        }
    },
    mounted () {
        fetch(this.uri)
        .then(res => res.json())
        .then(data => {
            console.log(data);
            this.title = data.title;
            this.details= data.details;            
        });
    }

}
</script>

<style>

</style>