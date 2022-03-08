<template>
    <nav>
        <router-lin to="/">
            <img :src="vueLogo" :alt="vueAlt" id="logo">
        </router-lin>
        <div class="menu">
           <router-link to="/"> <div class="pagesButton">Home</div></router-link>
            <router-link to="/orders"><div class="pagesButton">Pedidos</div></router-link>
            <router-link to="/about"><div class="pagesButton">Sobre</div></router-link>
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
        height: 150px;
        margin-left: auto;
        margin-right: auto;
        display: block;
    }

    nav {
        background-color: darkgrey;
        border-right: 2px solid;
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        font-size: 20px;
        width: 150px;
        align-content: center;
        height: 100%;
    }

    nav a {
        color: #222;
        text-decoration: none;
        text-align: center;
    }

    .pagesButton {
        position: relative;
        widows: 100%;
        text-align: center;
        padding: 10px;
        transition: 0.2s;
    }

    .pagesButton:hover {
        background-color: grey;
    }

    .menu {
        display: grid;
    }
</style>