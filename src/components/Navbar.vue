<template>
    <div id="nav">
        <router-link>
            <img :src="logo" :alt="alt" id="logo">
        </router-link>
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
    padding: 10px 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
#logo{
    width: 90px;
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