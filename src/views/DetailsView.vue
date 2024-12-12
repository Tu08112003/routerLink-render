<script setup>
import { useRoute } from "vue-router";
import {ref,onMounted} from "vue";

  const router = useRoute();
  const user = ref(null);
  onMounted(() => {
  fetch(`https://jsonplaceholder.typicode.com/users/${router.params.id}`)
    .then(response => response.json())
    .then(json => user.value = json)
    .catch(error => console.error("Error fetching user:", error));
});


</script>
<template>
  <div class="user-card">
    <h2>User Information</h2>
      <div class="user-details">
        <p><label>ID: {{user?.id}}</label></p>
        <p><label>Name: {{user?.name}}</label></p>
        <p><label>Username: {{user?.username}}</label></p>
        <p><label>Email: {{user?.email}}</label></p>
        <h3>Address</h3>
          <p class = "details-lv2"><label>Street: {{user?.address?.street}}</label></p>
          <p class = "detail-lv2"><label>Suite: {{user?.address?.suite}}</label></p>
          <p class = "detail-lv2"><label>City: {{user?.address?.city}}</label></p>
          <p class = "detail-lv2"><label>Zipcode: {{user?.address?.zipcode}}</label></p>
          <p class = "detail-lv2"><label>Geo: {{user?.address?.geo?.lat}}, {{user?.address?.geo?.lng}}</label></p>
          <p class = "detail-lv2"><label>Phone: {{user?.phone}}</label></p>
          <p class = "detail-lv2"><label>Website: {{user?.website}}</label></p>
        <h3>Company</h3>
          <p class = "detail-lv2"><label>Name: {{user?.company?.name}}</label></p>
          <p class = "detail-lv2"><label>CatchPhrase: {{user?.company?.catchPhrase}}</label></p>
          <p class = "detail-lv2"><label>BS: {{user?.company?.bs}}</label></p>
      </div>
  </div>
</template>

<style scoped>
  .user-card{
    display: grid;
    grid-template-rows: 3rem 2fr;
    margin: 2rem;
    border: 1px solid;
    border-radius: 10px;
    
  }
  .user-card h2{
    text-align: center;
    margin-top: 1rem;
  }
  .user-details{
    padding: 1rem 2rem;
  }
  .user-details .detail-lv2{
    margin-left: 1rem;
  }
  label{
    color: #2c3e50;
    font-size: 1.1rem;
  }
  h2{
    color: #2c3e50;
    font-weight: 500;
    font-size: 1.7rem;

  }
  h3{
    color: #2c3e50;
    font-weight: 400;
  }
</style>
