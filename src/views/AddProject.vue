<template>
  <form class= "form" @submit.prevent="handleSubmit">
      <label class="form__label"> Title:</label>
      <input class= "form__input" type="text" v-model="title" required>
      <label class="form__label">Details:</label>
      <textarea class="form__input" v-model="details" requried></textarea>
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
            fetch(process.env.VUE_APP_URL,{
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
   
</style>