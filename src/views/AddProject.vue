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

<style lang="scss">
.btn {
    &,
    &:link,
    &:visited {
    text-transform: uppercase;
    text-decoration: none;
    padding: 1.5rem 4rem;
    display: inline-block;
    border-radius: 10rem;
    transition: all .3s;
    position: relative;
    //  
    }

    &:hover {
        transform: translateY(-3rem);
        box-shadow: 0 .2rem .9rem rgba(black, .9);
            &::after {
                transform: scaleY(1.1) scaleX(1.1);                
               // opacity: 0;            
            }
        }
    &:active {
        transform: translateY(1rem);
        box-shadow: 0 .4rem .1rem rgba(black, 4);
        }
    &-white {
        background-color:white;
        color: #777;
        &::after {
            background-color:white;
        }
    }
    &::after {
        content: "";
        display: inline-block;
        height: 100%;
        width: 100%;
        border-radius: 10rem;
        position: absolute;
        top: 0;
        left: 0;
        z-index: -1;
        transition: all .01s;
    }

}
.animated_button {
    animation-name: moveUpbutton;
    animation-duration: .9s;
    animation-delay: .4s;
    animation-fill-mode: backwards;
}
.btn-text {
    &:link,
    &:visited {
        font-size: 1rem;
        color: blue;
        display: inline-block;
        text-decoration: none;
        border-bottom: 1px solid blue;
        padding: 3px;
        transition: all .2s;
    }
    &:hover {
        background-color: blue;
        color: white;
        box-shadow: 0 1rem 1rem rgba(black, .15);
        transform: translate(-2px);
    }
    &:active {
        box-shadow: 0 .5rem 1rem rgba(black, .15);
        transform: translateY(0);
    }
} 

    

</style>