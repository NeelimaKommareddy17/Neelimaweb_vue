<template>
    <div class="grid-container">
        <div v-for="hotel of hotelsList" :key="hotel.hotel_id">
            <SingleHotel :hotel = hotel />
        </div>
    </div>
</template>

<script>
    import SingleHotel from "./SingleHotel.vue";

    export default{
        name:"HotelsDirectory",
        components:{
            SingleHotel
        },
        props:{
            hotelsList:Array
        }
    }
</script>

<style scoped>
    .grid-container{
        display:grid;
        grid-template-columns:auto auto auto;
        gap:10px;
    }
</style>