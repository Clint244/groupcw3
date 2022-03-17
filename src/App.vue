<template>
    <div id="app">
      <header>
        <h3>{{sitename}}</h3>
        <button @click="showCheckout">{{this.cart.length}} Checkout</button>
      </header>
      <product-list :products ="products" @addProduct='addToCart'></product-list>
      <checkout :cart="cart" @removeProduct='removeFromCart'></checkout>
    </div>
</template>

<script>
import Checkout from './components/MyForm.vue'
import productList from './components/Products.vue'

export default {
  
        components: {
            productList,
            Checkout
        },
        name: "App",
        data() {
            return {
              sitename:"Afterschool Application",
                cart: [],
                products: [{
                        subject: "Ball",
                        location: "Malta",
                        price: 2500,
                        description: "Learn to play socer with us",
                        image: 'ball.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Basketball ",
                        location: "Malta",
                        price: 6700,
                        description: "Learn to play basketball with us",
                        image: 'bball.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Education",
                        location: "China",
                        price: 9010,
                        description: "Learn Education with us",
                        image: 'education.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "English",
                        location: "Surulere",
                        price: 2300,
                        description: "Learn English with us",
                        image: 'english.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Karate",
                        location: "Okota",
                        price: 5000,
                        description: "Learn Karate with us",
                        image: 'karate.jpg',
                        inventory: 10,
                        inCart: 0
                    },
                    {
                        subject: "Swimming",
                        location: "Ghana",
                        price: 980,
                        description: "Learn to Swim with us",
                        image: 'swim.jpg',
                        inventory: 10,
                        inCart: 0
                    }
                ]
            }
        },
        methods: {
            showCheckout: function(){
                    this.showProduct = this.showProduct ? false : true;
                },
            addToCart(product){
                let added = false;
                this.cart.forEach((product2) => {
                    if(product2.id === product.id){
                         product.inCart++
                         added = true
                    }
                });
                    if(!added){
                        this.cart.push(product)
                        product.inCart = 1
                    }    
                        product.inventory--; 
             
            },
            removeFromCart(product){
                this.cart.forEach((product2) => {
                    if(product2.id === product.id) {
                        product.inventory++;
                        product.inCart--
                    }
                })
            }    
        }
    }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>