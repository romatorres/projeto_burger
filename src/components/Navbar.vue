<template>
    <div id="nav">
        <div class="div-logo">
        <router-link>
            <img :src="logo" :alt="alt" id="logo">
        </router-link>
        <p class="text-logo">Burger<span> Top</span></p>
        </div>
        <div class="link">
            <router-link to="/">Home</router-link>
            <router-link to="/pedidos">Pedidos</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Navbar',
    props: ['logo', 'alt']
}
</script>

<style scoped>
#nav{
    background-color: #222;
    padding: 16px 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
#logo{
    width: 70px;
}
.div-logo{
    display: flex;
    align-items: center;
    gap: 10px;
}
.text-logo{
    color: #fff;
    font-size: 30px;
    font-weight: bold;
    text-align: left;
}
.text-logo span{
    color: #fcba03;
}
.link a{
    color: #fcba03;
    margin-left: 40px;
    text-decoration: none;
    font-size: 18px;
}
.link a:hover{
    color: #fff;
    transition: .5s;
}
</style>