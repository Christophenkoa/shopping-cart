<template>

    <div class="col-lg-3 col-md-4 col-sm-12">
        <div class="card mb-4" style="width: 18rem;">
            <img class="card-img-top" v-bind:src="product.image" :alt="product.id">
            <div class="card-body">
                <h5 class="card-title">{{product.name}}</h5>
                <p class="card-text">{{product.price}}</p>
                <a href="#" @click="addProduct(product.id)" class="btn btn-primary">Add to card</a>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: "Product",
        props: {
            product: Object,
        },
        methods: {
            addProduct(id) {
                // console.log(id);
                this.$emit('add-product', id);
            }
        }
    }
</script>

<style scoped>
img {
    height: 250px;
}
</style>