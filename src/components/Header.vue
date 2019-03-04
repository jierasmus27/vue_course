<template>
    <nav class="navbar navbar-default">
        <div class="container-fluid">
            <div class="navbar-header">
                <router-link class="navbar-brand" to="/">Brand</router-link>
            </div>

            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <router-link to="/portfolio" tag="li" activeClass="active"><a>Portfolio</a></router-link>
                    <router-link to="/stocks" tag="li" activeClass="active"><a>Stocks</a></router-link>
                </ul>
                <ul class="nav navbar-nav navbar-right">
                    <li><a href="#">End Day</a></li>
                    <li><a href="#">Save</a></li>
                    <li><a href="#">Load</a></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
export default {

}
</script>

