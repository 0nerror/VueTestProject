<template>
    <div id="warehouse">
        <h2>In Warehouse</h2>
            <ul>
                <li v-for="product in products" v-bind:key="product">
                    <input type="number" v-model.number="product.quantity">
                    {{ product.name }} 
                    <span v-if="product.quantity === 0">
                        - OUT OF STOCK
                    </span>
                    <button @click="product.quantity += 1">
                        +
                    </button>
                    <button @click="product.quantity -= 1">
                        -
                    </button>
                </li>
            </ul>
            <div class="totals">
                <h2>Total Inventory: {{ totalProducts }}</h2>
            </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
            products: []
            }
        },
        computed: {
            totalProducts () {
                return this.products.reduce((sum, product) => {
                    return sum + product.quantity
                }, 0)
            }
         },
        created () {
            fetch('http://api.myjson.com/bins/74l63')
                .then(response => response.json())
                .then(json => {
                this.products = json.products
            })
        }
    };
</script>

<style scoped>
    li {
    padding: 5px;
    }
    #warehouse h2 {
    text-align: left;
    margin-left: 5%;
    }
    #warehouse {
    margin-left: 45%;
    margin-right: 5%;
    border: 1px solid black;
    background-image: url("../assets/warehouse.png");
    background-size: 100% 100%;
    box-shadow: 5px 10px #888888;
    }
    #warehouse .totals h2 {
    text-align: right;
    margin-right: 5%;
    color: rgb(255, 255, 255);
    font-weight: bold;
    }
    input {
    text-align: center;
    color: tomato;
    margin-right: 5px;
    }
    button {
    box-shadow: 2px 2px;
    }
    span {
	color: red;
    }
</style>