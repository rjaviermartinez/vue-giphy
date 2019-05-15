<template>
    <div class="form">
        <h1>Giphy Search</h1>
        <form @submit.prevent="onSubmit">
            <input 
                type="text"
                v-model="nameImg"
            >

            <button

            >
                Buscar
            </button>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'GiphyForm',
        data()  {
            return {
                nameImg: ''
            }
        },
        methods: {
            onSubmit() {
                console.log('submited');
                this.$emit('searchGiphy', {
                    nameImg: this.nameImg
                });
            }
        }
    }
</script>


<style scoped>
    .form{
        background-color:#f5f5f5;
        border-radius: 10px;
        max-width: 500px;
        margin: 20px auto;
        padding: 20px;
    }

    .form input{
        display: block;
        width: 200px;
        height: 30px;
        margin: auto;
        margin-bottom: 10px;
        border: 1px solid #80bdff;
        border-radius: 5px;
        padding: 5px 10px;
        outline: 0;
        box-shadow: 0 0 0 1px rgba(0,123,255,.25);
    }

    .form button{
        background-color: dodgerblue;
        color: #fff;
        padding: 10px;
        width: 220px;
        border: none;
        border-radius: 5px;
        margin-top: 10px;
    }

    .form h1{
        margin: 0;
    }

    .form button:hover{
        cursor: pointer;
        opacity: .9;
    }

</style>
