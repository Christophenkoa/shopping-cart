<template>
    <div class="item" :key="product.id" v-for="product in products">
        <Product @add-product="$emit('add-product', product.id)" :product="product"/>
    </div>
</template>

<script>
    import Product from "./Product";
    export default {
        name: "Products",

        props: {
            products: Array,
        },

        components: {
            Product,
        },
        emits: ['add-product'],
    }
</script>

<style scoped>
.item {
    margin: auto;
}
</style>