<template>
    <div class="col-sm-6 col-md-4">
        <div class="panel panel-success">
            <div class="panel-heading">
                <h3 class="panel-title">
                    {{ stock.name }}
                    <small>(Price: {{ stock.price }})</small>
                </h3>
            </div>
            <div class="panel-body">
                <div class="pull-left">
                    <input
                        type="number"
                        class="form-control"
                        placeholder="Quantity"
                        v-model="quantity">
                </div>
                <div class="pull-right">
                    <button
                        class="btn btn-success"
                        @click="buyStock"
                        :disabled="inValid">
                        Buy
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            quantity: 0
        }
    },
    props: ['stock'],
    methods: {
        buyStock() {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            this.$store.dispatch('buyStock', order);
            this.quantity = 0;
        },
    },
    computed: {
        funds() {
            return this.$store.getters.funds;
        },
        inValid() {
            return this.quantity <= 0 || !Number.isInteger(+this.quantity) || (this.quantity * this.stock.price) > this.funds
        }
    }
}
</script>
