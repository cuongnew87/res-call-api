<template>
    <Header/>
    <h1>Add Restaurant Page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
        <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact" />
        <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address" />
        <button type="button" v-on:click="addRestaurant">Add new Restaurant</button>
    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios';
export default {
    components: { Header },
    name:"Add",
    data(){
        return{
            restaurant:{
                name:'',
                contact:'',
                address:'',
            }
        }
    },
    methods:{
        async addRestaurant(){
            let result = await axios.post("https://6153335e3f4c430017159234.mockapi.io/restaurant",{
                name: this.restaurant.name,
                contact: this.restaurant.contact,
                address: this.restaurant.address
            });

            if(result.status === 201){
                alert("Success");   
                this.$router.push({name:'Home'});
            }
        }
    }
}
</script>

<style>

</style>