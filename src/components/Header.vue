<template>
    <nav class="navbar navbar-default">
        <div class="container-fluid">
            <div class="navbar-header">
                <router-link class="navbar-brand" to="/">Brand</router-link>
            </div>
            <strong class="navbar-text navbar-right">Funds: {{ funds | currency }}</strong>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <router-link to="/portfolio" tag="li" activeClass="active"><a>Portfolio</a></router-link>
                    <router-link to="/stocks" tag="li" activeClass="active"><a>Stocks</a></router-link>
                </ul>
                <ul class="nav navbar-nav navbar-right">
                    <li><a href="#" @click="endDay">End Day</a></li>
                    <li><a href="#" @click="saveData">Save</a></li>
                    <li><a href="#" @click="loadData">Load</a></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
import {mapActions} from 'vuex';

export default {
    computed: {
        funds() {
            return this.$store.getters.funds;
        }
    },
    methods: {
        ...mapActions({
            randomizeStocks: 'randomizeStocks',
            fetchData: 'loadData'
        }),
        endDay() {
            this.randomizeStocks();
        },
        saveData() {
            const data = {
                funds: this.$store.getters.funds,
                stockPortfolio: this.$store.getters.stockPortfolio,
                stocks: this.$store.getters.stocks
            };

            this.$http.put('data.json', data);
        },
        loadData() {
            this.fetchData();
        }
    }

}
</script>

