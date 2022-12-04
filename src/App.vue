<template>
 
  <link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin><link href="https://fonts.googleapis.com/css2?family=Inter&display=swap" rel="stylesheet">
  
  
  <div class="whole-page">
    <ProductDisplayVue />
    

  </div>
  
  
  
</template>

<script>
import ProductDisplayVue from './components/ProductDisplay.vue';
export default {
  name: 'App',
 
  components: {
    ProductDisplayVue
  },
  
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}



.featured-image{
  background-image:url("./assets/bg-pattern.png");
  width: 100%;
  /* z-index: 3; */
}

.rectangle-7.unavailable{
  background-image: url("./assets/sad-face.png");
  float: inline-start;
  background-size: 1300px 580px;
  /* width: 1500px; */
  /* height: 580px; */
  /* width: 200%; */
  /* height: 100%; */
}


</style>