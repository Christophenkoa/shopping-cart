<template>

    <div class="container">

        <Header/>

        <div class="title">
            Our products
        </div>

        <div class="row clearfix">
            <Products @add-product="addProduct" :products="products"/>
        </div>

    </div>

    <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-body">
                    <Card v-bind:items="userItems"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import Card from "./components/Card";
import Products from "./components/Products";
import Header from "./components/Header";
export default {
  name: 'App',
  components: {
      Products,
      Card,
      Header,
  },
    props: {},

    data() {
      return {
          userItems: [],
          products: [],
      };
    },

    methods: {
      addProduct(id) {
          this.products.map((product) => {
              if(product.id === id) {

                  this.userItems.push(product);
              }
          });
          console.log(this.userItems);
      }
    },

    created() {
        this.userItems = [];
        this.products = [
            {
                id: 1,
                name: "television",
                min_qty: 1,
                image: "https://www.sencor.com/Sencor/media/static-media/0c97698f-45fe-4e28-ad75-eb6d10f93b9b@w600.webp",
                price: 50000
            },
            {
                id: 2,
                name: "phone",
                min_qty: 1,
                image: "https://images.frandroid.com/wp-content/uploads/2020/10/iphone-12-frandroid-2020.png",
                price: 70000
            },
            {
                id: 3,
                name: "laptop",
                min_qty: 1,
                image: "https://id-media.apjonlinecdn.com/catalog/product/cache/b3b166914d87ce343d4dc5ec5117b502/c/0/c06624403_4.png",
                price: 500000
            },
            {
                id: 4,
                name: "watch",
                min_qty: 1,
                image: "https://cdn.shopify.com/s/files/1/0057/8938/4802/products/485ea9aa-b170-4efc-ac40-ab8b0854083c.png?v=1625046257",
                price: 8000
            },
            {
                id: 5,
                name: "watch",
                min_qty: 1,
                image: "https://mi-store.ma/wp-content/uploads/2021/02/pms_1607424380.42925824.png",
                price: 9000
            },
            {
                id: 6,
                name: "watch",
                min_qty: 1,
                image: "https://cdn.shopify.com/s/files/1/0057/8938/4802/products/485ea9aa-b170-4efc-ac40-ab8b0854083c.png?v=1625046257",
                price: 8500
            },
        ]
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
}


.flex-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}

.title {
    font-size: 2em;
    font-family: Helvetica,serif;
    font-weight: bold;
    margin-bottom: 20px;
}

img {
    height: 5%;
    width: 5%;
}
</style>
