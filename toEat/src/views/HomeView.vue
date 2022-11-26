<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import { ref } from 'vue';
 
const restaurantList = ref<Restaurant[]>([])
const newRestaurant = ref<Restaurant>({})

type RestaurantStatus = | '1 star' | '2 stars' | '3 stars'


interface Restaurant{
  name?:string,
  adress?:string,
  status?:RestaurantStatus,
  dishes?:Dish[]
}

const statusList = ['1 star',' 2 stars',' 3 stars',' 4 stars', '5 stars']

function addRestaurant(){
  restaurantList.value.push(
    {
      adress:"",
      dishes:[],
      name:newRestaurant.value.name,
      status:'1 star'
    }
  )
}
</script>

<template>
  <main>
    <form @submit.prevent="addRestaurant">
      <label for="restaurant-name">Restaurant Name</label>
      <input id="restaurant-name" v-model="newRestaurant.name" type="text"/>

      <label for="restaurant-adress">Restaurant Adress</label>
      <input id="restaurant-adress" v-model="newRestaurant.adress" type="text"/>

      <label for="restaurant-status">Restaurant Status</label>
      <select name="restaurant-status" id="restaurant=status" v-model="newRestaurant">
        <option v-for="status in statusList" value="status" key="status">{{status}}</option>
      </select> 

      <button type="submit">Add Restaurant</button>
        
    </form>

    <ul>
      <li v-for="restaurant in restaurantList" key="restaurant">{{restaurant.name}}</li>
    </ul>
  </main>
</template>
