<template>
    <div class="main_banner">
        <h1>App For Burger!! Um app para Hamburgerias, descomplicado e inteligente!</h1>
    </div>
</template>

<script>
export default {
    name: "Banner",
}
</script>

<style scoped>
.main_banner{
    background-image: url('/public/img/burger.jpg');
    background-position: 0 -310px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: start;
}
.main_banner h1{
    font-size: 56px;
    color: #fff;
    text-align: left;
    padding: 20px 100px;
    max-width: 700px;

}
</style>