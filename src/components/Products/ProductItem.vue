<template>
   
    <div class="products">
      <div class="product-item" v-for="(product,index) in products" :key="index">
      <h2>{{ product.name }}</h2>
      <img :src="product.image" alt="">
      <div> Cost : {{ product.price }}</div>
      <button @click="addTocart(product)">Add to Cart</button>
      </div>
    </div>
    </template>
    
    <script>


   
    export default {
        props:{
        cart:{
            type : Array,
            required: true,
        },
        products :{
          type: Array,
          required :true
        }
    },
      data(){
        return {
          
         
        }
      },
     
      methods :{
        addTocart(product){
            this.$emit('addToCart' , product)

        }
      },
    
  //   mounted() {
  //   this.products();
  // },
}
    </script>
    
<style scoped>
    .products{
        display: flex;
        margin: 50px;
        flex-wrap: wrap;
        padding: 10px;
        align-items: center;
        justify-content:space-around;
    }
    h2{
        padding: 10px;
    }
    img{
        height: 200px;
    }
.product-item {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  width: 33%;
}
.product-item:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

button{
    margin-top: 5px;
    margin-bottom: 5px;
    background-color: #222;
  border-radius: 4px;
  border-style: none;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: "Farfetch Basis","Helvetica Neue",Arial,sans-serif;
  font-size: 16px;
  font-weight: 700;
  line-height: 1.5;
  margin: 0;
  max-width: none;
  min-height: 44px;
  min-width: 10px;
  outline: none;
  overflow: hidden;
  padding: 9px 20px 8px;
  position: relative;
  text-align: center;
  text-transform: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  width: 100%;
}



 </style>
