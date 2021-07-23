<template>
    <div class="card">
        <div v-if="items.length === 0"> Empty Cart </div>
        <div v-else class="row">
            <div class="col-md-12 cart">

                <div class="title">
                    <div class="row">
                        <div class="col">
                            <h4><b>Shopping Cart</b></h4>
                        </div>
                        <div class="col align-self-center text-right text-muted">{{items.length}} items</div>
                    </div>
                </div>

                <div class="row border-bottom" :key="item.id" v-for="item in items">
                    <div class="row main align-items-center">
                        <div class="col-2"><img class="img-fluid" :src="item.image" :alt="item.name"></div>
                        <div class="col">
                            <div class="row"> {{item.name}}</div>
                        </div>

                        <div class="col">
                            <a @click="decreaseQty(item)">-</a>
                            <a class="border"> {{item.min_qty}}</a>
                            <a @click="increaseQty(item)">+</a>
                        </div>

                        <div class="col">XAF {{item.price}} <span class="close" @click="removeItem(items, item.id)">&#10005;</span></div>
                    </div>
                </div>

                <div class="row" style="border-top: 1px solid rgba(0,0,0,.1); padding: 2vh 0;">
                    <div class="col">TOTAL PRICE</div>
                    <div class="col text-right">XAF {{totalPrice(items)}}</div>
                </div>

            </div>
            <button type="button" class="btn btn-primary">Checkout</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Card",
        props: {
            items: Array,
        },
        methods: {
            totalPrice (items) {
                let sum = 0;
                for (let i = 0; i < items.length; i++) {
                    sum += items[i].price * items[i].min_qty;
                }
                return sum;
            },

            increaseQty(item) {
                item.min_qty ++;
                console.log(item);
            },

            decreaseQty(item) {

                // some works should be add here
                if(item.min_qty > 0) {
                    item.min_qty --;

                }else {
                    alert("You cannot reduce less than the minimum price");
                }
            },

            // work need to be done here
            removeItem(items, id) {
                if(confirm('Are you sure ?')) {
                    // items.filters( (item) => item.id !== id );
                    console.log(id);
                    console.log(items);
                }
            }
        },
        //emits: ['increase-quantity', 'decrease-quantity'],
    }
</script>

<style scoped>
    body {
        background: #ddd;
        min-height: 100vh;
        vertical-align: middle;
        display: flex;
        font-family: sans-serif;
        font-size: 0.8rem;
        font-weight: bold
    }

    .title {
        margin-bottom: 5vh
    }

    .card {
        margin: auto;
        max-width: 950px;
        width: 90%;
        box-shadow: 0 6px 20px 0 rgba(0, 0, 0, 0.19);
        border-radius: 1rem;
        border: transparent
    }

    @media(max-width:767px) {
        .card {
            margin: 3vh auto
        }
    }

    .cart {
        background-color: #fff;
        padding: 4vh 5vh;
        border-bottom-left-radius: 1rem;
        border-top-left-radius: 1rem
    }

    @media(max-width:767px) {
        .cart {
            padding: 4vh;
            border-bottom-left-radius: unset;
            border-top-right-radius: 1rem
        }
    }

    .summary {
        background-color: #ddd;
        border-top-right-radius: 1rem;
        border-bottom-right-radius: 1rem;
        padding: 4vh;
        color: rgb(65, 65, 65)
    }

    @media(max-width:767px) {
        .summary {
            border-top-right-radius: unset;
            border-bottom-left-radius: 1rem
        }
    }

    .summary .col-2 {
        padding: 0
    }

    .summary .col-10 {
        padding: 0
    }

    .row {
        margin: 0
    }

    .title b {
        font-size: 1.5rem
    }

    .main {
        margin: 0;
        padding: 2vh 0;
        width: 100%
    }

    .col-2,
    .col {
        padding: 0 1vh
    }

    a {
        padding: 0 1vh
    }

    .close {
        margin-left: auto;
        font-size: 0.7rem
    }

    img {
        width: 3.5rem
    }

    .back-to-shop {
        margin-top: 4.5rem
    }

    h5 {
        margin-top: 4vh
    }

    hr {
        margin-top: 1.25rem
    }

    form {
        padding: 2vh 0
    }

    select {
        border: 1px solid rgba(0, 0, 0, 0.137);
        padding: 1.5vh 1vh;
        margin-bottom: 4vh;
        outline: none;
        width: 100%;
        background-color: rgb(247, 247, 247)
    }

    input {
        border: 1px solid rgba(0, 0, 0, 0.137);
        padding: 1vh;
        margin-bottom: 4vh;
        outline: none;
        width: 100%;
        background-color: rgb(247, 247, 247)
    }

    input:focus::-webkit-input-placeholder {
        color: transparent
    }

    .btn {
        color: white;
        width: 100%;
        font-size: 0.7rem;
        margin-top: 4vh;
        padding: 1vh;
    }

    .btn:focus {
        box-shadow: none;
        outline: none;
        box-shadow: none;
        color: white;
        -webkit-box-shadow: none;
        -webkit-user-select: none;
        transition: none
    }

    .btn:hover {
        color: white
    }

    a {
        color: black
    }

    a:hover {
        color: black;
        text-decoration: none
    }

    #code {
        background-image: linear-gradient(to left, rgba(255, 255, 255, 0.253), rgba(255, 255, 255, 0.185)), url("https://img.icons8.com/small/16/000000/long-arrow-right.png");
        background-repeat: no-repeat;
        background-position-x: 95%;
        background-position-y: center
    }
</style>