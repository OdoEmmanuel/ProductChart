<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">  Product component </div>

                    <div class="card-body">

                        <form @submit.prevent="createProduct">
                            <div class="form-group">
                                <label for="name">Name</label>
                                <input v-model="product.name" type="text" id="name" class="form-control">
                            </div>


                            <div class="form-group">
                                <label for="year">Year</label>
                                <input v-model="product.year" type="number" id="year" class="form-control">
                            </div>

                            <div class="form-group">
                                <label for="price">Price</label>
                                <input v-model="product.price" type="number" id="price" class="form-control">
                            </div>

                            <div class="form-group">
                                <button class="btn btn-primary">Create Product</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                product: {},
            }
        },

        mounted() {
            console.log('Component mounted.')
        },
        methods: {
            createProduct(){
                axios.post('/products', this.product)
                .then((response) =>{
                    window.location.reload();
                });
                console.log(this.product)
            }
        }
    }
</script>
