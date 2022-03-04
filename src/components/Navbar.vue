<template>
    <nav>
        <router-lin to="/">
            <img src="" id="logo">
        </router-lin>
        <router-link to="/">Home</router-link> |
        <router-link to="/orders">Pedidos</router-link> |
        <router-link to="/about">Sobre</router-link>
    </nav>
</template>

<script>
export default {
    name: 'navbar'
}
</script>

<style scoped>

</style>