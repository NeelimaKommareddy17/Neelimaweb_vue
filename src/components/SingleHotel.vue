<template>
    <div class="hotel_card">
        <div class="hotel_photo">
            <img :src=hotel.hotel_image alt="Hotel Photo"/>
        </div>
        <div class="hotel_details">
            <h3>{{hotel.hotel_name}}</h3>
            <p class="gray"><img src="https://img.icons8.com/?size=20&id=85149&format=png" alt="Location Icon"/>{{hotel.hotel_location}}</p>
            <hr>
            <div class="flex-container">
                <p class="gray">{{hotel.hotel_roomType}}</p>
                <p class="price">{{hotel.hotel_price}}$</p>
            </div>
            <hr>
            <div class="flex-container">
                <p class="gray">{{hotel.hotel_checkin_time}}</p>
                <p class="gray">{{hotel.hotel_checkout_time}}</p>
                <p class="status" :style="{backgroundColor: this.getHotelStatus(hotel.hotel_bookingStatus)}">{{hotel.hotel_bookingStatus}}</p>
            </div>
            <hr>
            <div class="flex-container">
                <p class="gray"><img src="https://img.icons8.com/?size=20&id=5402&format=png" alt="Contact Icon"/>{{hotel.hotel_contact}}</p>
                <StarRating read-only :rating="hotel.hotel_rating" :star-size="20" active-color="gold"/>
            </div>
        </div>
    </div>
</template>

<script>
    import StarRating from "vue-star-rating";

    export default{
        name: "SingleHotel",
        components:{
            StarRating
        },
        props:{
            hotel:Object
        },
        methods:{
            getHotelStatus(availability){
                if(availability === "Available") return "#81b29a";
                else if(availability === "Limited availability") return "#f4845f";
                else return "#bc4b51";
            }
        }
    }
</script>

<style scoped>
    .hotel_card{
        display:flex;
        flex-direction:column;
        justify-content:space-between;
        align-content:center;
         border:transparent;
        border-radius:4px;
        padding:10px;
        box-shadow:0 4px 8px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
    }
    .hotel_photo{
        width:100%;
    }
    .hotel_photo img{
        width:100%;
        height:250px;
    }
    .hotel_details img{
        vertical-align: middle; 
    }
    .flex-container{
        display:flex;
        justify-content:space-between;
        align-items:center;
    }
    .gray{
        color:#495057;
        font-weight:bold;
    }
    .status{
        border:transparent;
        border-radius: 5px;
        padding:9px;
        color:white;
    }
    .price{
        font-weight:bold;
        font-size: 1.2rem;
    }
</style>