<template>
<header>
    <div class="header">
        <h1>{{ page }}</h1>
    </div>
    <div v-if="page==='cart'" class="view-product">
        <h1 @click="togglePage()">View all Products</h1>
    </div>
    <div class="cartDetails">
    <img @click="togglePage()" src="../../assets/shopping-basket.png" alt="">
    <span>{{ cart.length  }}</span>
    </div>
   
   
</header>
</template>


<script>

export default{
    props:{
        cart:{
            type : Array,
            required: true,
        },
        page:{
            type : String,
            required: true,
        }
    },
    methods:{
        togglePage(){
            this.$emit("togglePage")
        }
       
    }
}
</script>

<style scoped>
header{
   
    display: flex;
    align-items: center;
    justify-content: space-around;
}
img{
    height: 20px;
    margin: 2px;
}
span{
    font-size: 20px;
    margin: 2px;
    
}
.header{
    display: flex;
  
    width: 70%;
    align-items: center;
    justify-content: center;
}
.cartDetails{
   
}
 </style>