<template>
  <HotelHeader/>
  <HotelsDirectory :hotelsList = hotelsList />
</template>

<script>
  import HotelHeader from "./components/HotelHeader.vue";
  import HotelsDirectory from "./components/HotelsDirectory.vue";

  export default{
    name: "App",
    components:{
      HotelHeader,
      HotelsDirectory
    },
    data(){
      return{
        hotelsList:[]
      }
    },
    methods:{
      async fetchHotelsList(){
        const response = await fetch("https://neelimaweb-node.onrender.com/api");
        const hotelsData = await response.json();
        console.log(hotelsData[0].hotels);
        return hotelsData[0].hotels;
      },
    },
    async created(){
        this.hotelsList = await this.fetchHotelsList();
      }
  }
</script>

<style scoped>
</style>