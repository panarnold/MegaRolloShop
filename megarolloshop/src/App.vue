<template>
<Header/>
  <div id="app">
    <Cart :list="list" @remove-item="removeItem($event)" @remove-all="removeAll()"/>
    <h2> Cost: {{totalCost}} PLN</h2>
    <h1> Menu: </h1>
    <Menu :menu="menu" @add-to-cart="addToCart($event)"/>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';
import {reduce} from "lodash";
import Cart from './components/Cart.vue';
import Menu from './components/Menu.vue';

export default {
  name: 'App',
  components: {
    Menu,
    Header,
    Cart
  },
  data() {
    return{
            menu: [
                {
                    id: 1,
                    name: "Medium Rollo",
                    price: 15
                },
                {
                    id: 2,
                    name: "Just Rollo",
                    price: 20
                },
                {
                    id: 3,
                    name: "Double Meat Rollo",
                    price: 25
                },
                {
                    id: 4,
                    name: "Your Mama Rollo (giant)",
                    price: 30
                }
            ],
            list: [

            ]
                
            
        }
  },
  methods: {
    addToCart(item) {
      this.list = [...this.list, item];
      console.log(item);
    },
    removeItem(id) {
        this.list = this.list.filter(list => list.id !== id);
      },
    removeAll() {
      this.list = [];
    }
    },
  computed: {
    totalCost() {
        return reduce(
          this.list,
          (total, item) => total + item.price,
          0
          );
      
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
