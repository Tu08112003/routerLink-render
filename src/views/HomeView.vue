<script setup>
import { computed, onMounted, ref } from "vue";
import { useRouter } from "vue-router";

  const users = ref([]);
  const txtSearch = ref('')
  onMounted(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(json => users.value = json)
  });

  const filterUser = computed(() => {
    return users.value.filter(item => item.name.toUpperCase().indexOf(txtSearch.value.toUpperCase()) != -1 || item.email.toUpperCase().indexOf(txtSearch.value.toUpperCase()) != -1)
  })

  const router = useRouter();
</script>

<template>
<div class="main">
  <div class="input-search">
      <input type="text" placeholder="Search here..." v-model="txtSearch"/>
    </div>
    <div class="card-view">
      <div class="card-item" 
        v-for="user in filterUser"
        v-on:click="router.push({ path: `/details/${user?.id}` })"
        >
      <h3>Name: {{ user?.name }}</h3> 
      <h5>Email: {{ user?.email }}</h5> 
    </div>
    </div>
</div>

</template>
<style scoped>
.main{
  padding: 0.5rem 2rem;
  display: grid;
  grid-template-rows: 0.5fr 2fr;
}
.input-search{
  display: flex;
  justify-content: center;
  align-items: center;
}
.input-search input{
  padding: 0.5rem 1rem;
  width: 80%;
  border-radius: 5px;
}

.card-view{
  padding: 1rem 1rem;
  max-height: 29rem;
  overflow-y: auto;
  border: 1px solid;
  border-radius: 10px;
}
.card-view .card-item{
  color: #333;  
  border-radius: 5px;
  padding: 1rem;
  margin: 0.7rem;
  background-color: #fff; 
  border-radius: 10px;
  border: 1px solid;
  box-shadow: 0.4rem 0.4rem 0.2rem rgb(0,0,0,0.2);

}
.card-view .card-item:hover{
  background-color: #dbdbdb; 
}
</style>
