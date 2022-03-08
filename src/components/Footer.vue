<template>
    <footer>
        <p>Faça sua Pizza Top &copy; 2021</p>
    </footer>
</template>


<script>
export default {
    name: 'footer'
}
</script>


<style scoped>
    footer {
        position: fixed;
        bottom:0;
        left:0;
        background-color: rgb(114, 114, 114);  
        width: 100%;
        height: 50px;
        border-top: 2px solid;
    }

    footer p {
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 15px;
    }
</style>