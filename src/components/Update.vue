<template>
    <Header/>
    <h1>Update Restaurant Page</h1>
    <form class="update">
        <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name" />
        <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact" />
        <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address" />
        <button type="button" v-on:click="updateRestaurant">Update Restaurant</button>
    </form>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
    components: { Header },
    name:"Update",
    data(){
        return{
            restaurant:{
                name:'',
                contact:'',
                address:'',
            }
        }
    },
    async mounted(){
        let result = axios.get(`https://6153335e3f4c430017159234.mockapi.io/restaurant/`+this.$route.params.id);
        console.log(result);
        this.restaurant = (await result).data;
    },
    methods:{
        async updateRestaurant(){
            let result = await axios.put("https://6153335e3f4c430017159234.mockapi.io/restaurant/"+this.$route.params.id,{
                name: this.restaurant.name,
                contact: this.restaurant.contact,
                address: this.restaurant.address
            });

            console.log(result);
            if(result.status === 200){
                alert("Success");   
                this.$router.push({name:'Home'});
            }
        }
    }
}
</script>

<style>

</style>