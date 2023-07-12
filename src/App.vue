<template>
<TheHeader :page="page" :cart="cart" @togglePage="togglePage"></TheHeader>
<ProductItem v-if="page==='product'" :cart="cart" @addToCart="addToCart"></ProductItem>
<CartPage v-if="page==='cart'"   :cart="cart"  @removeFromCart="removeFromCart"></CartPage>

</template>

<script>
 import TheHeader from "../src/components/UI/TheHeader.vue"
import ProductItem from "./components/Products/ProductItem.vue"
import CartPage from "./components/ShoppingCart/CartPage.vue"
export default{
 components :{
  ProductItem,
  CartPage,
  TheHeader
 } ,
 data (){
  return {
    page : "product",
    cart :[]
  }
 },
 methods :{
  togglePage(){
    if(this.page === "product"){
      this.page = "cart"
    }else if (this.page === "cart"){
      this.page = "product"
    }
  },
  addToCart(product){
    this.cart.push(product)
  },
  removeFromCart(productIdx){
    console.log(productIdx)
     this.cart.splice(productIdx, 1)
 //console.log(this.cart);
  //console.log(product)
  }
 }

 }


</script>


<style>
*{
  padding: 0px;
  margin: 0px;
  box-sizing: border-box; 
}

</style>