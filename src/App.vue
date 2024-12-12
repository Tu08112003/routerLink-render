<script>

</script>
import { RouterLink, RouterView } from 'vue-router'

<template>
  <header>
    <img class="logo" src="../src/assets/logo.svg" alt="">
      <nav>
        <button><RouterLink to="/">Home</RouterLink></button>
        <!-- <button><RouterLink to="/details">Details</RouterLink></button> -->
      </nav>
  </header>
  <RouterView />
</template>

<style scoped>

header{
  display: flex;
  flex-direction: column;
  padding: 2rem;
  align-items: center;
  justify-content: center;
  border-right: 1px solid;
  border-radius: 10px;
}
.logo {
  display: block;
  width: 7rem;
  height: 7rem;  
}
nav{
  display: flex;
  margin-top: 2rem;
  gap: 1rem;
}
nav a {
  text-decoration: none;
  color: #fff;

}
button{
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  font-weight: bold;
  box-shadow: 0.2rem 0.3rem #ccc;
  transition: all 0.3s ease;
  background-color: #4CAF50; 
  text-decoration: none;
}
button:hover{
  box-shadow: 0.2rem 0.3rem #aaa;
  background-color: #45a049; 
}
</style>
