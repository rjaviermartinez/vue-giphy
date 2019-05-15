<template>
  <div id="app">
    <img class="vueLogo" alt="Vue logo" src="./assets/logo.png">
    <GiphyForm
      @searchGiphy="searchGiphy"
    />

    <ul>
      <li 
        v-for="image in images"
        v-bind:key="image.id" 
      >
        <a
          v-bind:href="image.url"
          target="_blank"
        >
          <img
            v-bind:src="image.images.preview_gif.url"
          />
        </a>
      </li>
    </ul>

  </div>
</template>

<script>
import GiphyForm from './components/GiphyForm.vue'
import Axios from 'axios';

export default {
  name: 'app',
  components: {
    GiphyForm
  },
  data() {
    return {
      images: []
    }
  },
  methods: {
    searchGiphy(obj) {
      const q = obj.nameImg;

      const url = 'https://api.giphy.com/v1/gifs/search?api_key=yvwA8IzIyat8LWFNiIbVz6BqNGAz6n8N&q='+q+'&limit='+obj.quantity+'&offset=0&rating=G&lang=en';

      Axios.get(url).then(
        (res) =>{
          console.log('res');
          console.log(res.data.data);
          console.log('this.images');
          this.images = res.data.data;
          console.log(this.images);
      })
      .catch(error => {
          console.log(error.response)
      });

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
img.vueLogo{ max-width: 70px; }
ul li{
  list-style: none;
  display: inline-block;
}

ul li img{
  width: auto;
  max-width: 100px;
  margin-right: 10px;
}
</style>
