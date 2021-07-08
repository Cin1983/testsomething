<template>
  <div id="app">
    <div class="container">
      <div class="button-wrapper">
        <button class="btn" @click="searchUnsplash('Cars')">CARS</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
//constructor function
export default {
  name:'App',
  methods:{
searchUnsplash(topic){
  this.images=[];
  axios.get(`https://api.unsplash.com/search/photos?query=${topic}&per_page=20`,
  {headers:{
    Authorization:"Client-ID oozTUUGcoOmOleTWzWgrDTU04NmhO8a-pxF5TmPPNKw",
    "Accept-Version":"v1"
    }
  }
)
.then(response =>{
  this.images=response.data.results;
})
.catch(()=>{
  this.images=[]
  });
    }
  }
}
</script>

<style>
.container {
  width: 80vw;
  margin: 0 auto;
}
.button-wrapper {
  display: flex;
  justify-content: center;
  margin-bottom: 25px;
}
.btn {
  font-size: 18px;
  background-color: #42b983;
  color: white;
  padding: 10px 20px;
}

</style>
