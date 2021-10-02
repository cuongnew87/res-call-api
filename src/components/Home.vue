<template>
<Header />
<h1>This is Home page</h1>
<table border="1">
    <tr>
        <td>ID</td>
        <td>Name</td>
        <td>Contact</td>
        <td>Address</td>
        <td>Action</td>
    </tr>
    <tr v-for="item in restaurant" :key="item.id">
        <td>{{item.id}}</td>
        <td>{{item.name}}</td>
        <td>{{item.contact}}</td>
        <td>{{item.address}}</td>
        <td>
            <router-link :to="'/update/' + item.id">Update</router-link>
            <button v-on:click="deleteRestaurant(item.id)">Delete</button>
        </td>
    </tr>
</table>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
  components: { Header },
    name:'Home',
    data(){
        return{
            name:'',
            restaurant:[]
        }
    },
    mounted(){
        this.loadData();
    },
    methods:{
        async deleteRestaurant(id){
            let result = axios.delete(`https://6153335e3f4c430017159234.mockapi.io/restaurant/`+id);

            if((await result).status == 200){
                alert("Delete success");
                this.loadData();
            }
        },
        async loadData(){
            let result = axios.get(`https://6153335e3f4c430017159234.mockapi.io/restaurant`);
            this.restaurant = (await result).data;
        }
    }
}
</script>

<style>
td{
    width: 160px;
    height: 40px;
}
</style>