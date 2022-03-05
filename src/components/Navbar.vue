<template>
    <nav>
        <router-lin to="/">
            <img :src="vueLogo" :alt="vueAlt" id="logo">
        </router-lin>
        <router-link to="/">Home</router-link>
        <router-link to="/orders">Pedidos</router-link>
        <router-link to="/about">Sobre</router-link>
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
    }

    nav {
        background-color: darkgrey;
        border-right: 3px solid;
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        font-size: 20px;
        padding: 15px 50px;
        display: grid;
        max-width: 150px;
        align-content: center;
        position: fixed;   
        float: left;  
        height: 100%;
    }
</style>