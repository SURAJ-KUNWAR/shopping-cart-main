<template>
    <div class="cart">
        
      <div class="cartItem" v-for="(product,idx) in cart" :key="idx">
      <h2>{{ product.name }}</h2>
      <img :src="product.image" alt="">
      <div> Cost : {{ product.price }}</div>
      <h4>Quantity : {{ product.quantity }}</h4>
      <button @click="removeFromCart(idx)">Remove From Cart</button>
      </div>
      <h3>CartTotal : {{ totalCostt }}</h3>
    </div>
</template>
<script>

export default{
    data(){
        return {
            totalCost : 0,
        }
    },
    props:{
        cart :{
            type : Array,
            required: true,
        }
    },
    methods :{
        removeFromCart(productIdx){
            this.$emit('removeFromCart' , productIdx)
            console.log(this.cart);

        }, 
      },
    computed: {
    totalCostt() {
      return this.cart.reduce((accumulator, item) => {
        return accumulator + item.price;
      }, 0);
    }
  }  
    
    
}
</script>


<style scoped>
.cart{
        display: flex;
        flex-wrap: wrap;
        margin: 50px;
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
.cartItem {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.cartItem:hover {
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