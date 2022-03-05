<template>
    <nav>
        <router-lin to="/">
            <img :src="vueLogo" :alt="vueAlt" id="logo">
        </router-lin>
        <div class="menu">
            <router-link to="/">Home</router-link>
            <router-link to="/orders">Pedidos</router-link>
            <router-link to="/about">Sobre</router-link>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'navbar',
    props: ['vueLogo', 'vueAlt']
}
</script>

<style scoped>
    #logo {
        height: 100px;
        padding: 0px 0px 0px 20px;
    }

    nav {
        background-color: darkgrey;
        border-right: 3px solid;
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        font-size: 20px;
        width: 150px;
        align-content: center;
        height: 100%;
    }

    .menu {
        display: grid;
        padding: 15px;
    }
</style>