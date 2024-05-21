<template>
    <p>Componente de messagem</p>
    <form id="burger-form">
        <div class="input-container">
            <label for="nome">Nome do cliente</label>
            <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digete seu nome">
        </div>
        <div class="input-container">
            <label for="pao">Escolha o pão</label>
            <select name="pao" id="pao" v-model="pao">
                <option value="">Selecione o pão</option>
                <option value="integral">Integral</option>
            </select>
        </div>
        <div class="input-container">
            <label for="carne">Escolha a carne</label>
            <select name="carne" id="carne" v-model="carne">
                <option value="">Selecione a carne</option>
                <option value="integral">Integral</option>
            </select>
        </div>
        <div class="input-container" id="opcionais-container">
            <label id="opcionais-title" for="opcionais">Escolha os opcionais</label>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" value="salame" v-model="opcionais">
                <span>Salame</span>
            </div>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" value="salame" v-model="opcionais">
                <span>Salame</span>
            </div>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" value="salame" v-model="opcionais">
                <span>Salame</span>
            </div>
        </div>
        <div class="input-container">
            <input type="submit" value="Criar seu Burger" class="submit-btn">
        </div>
    </form>
</template>

<script>
export default {
    nome: 'BurgerForms'
}
</script>

<style scoped>
    #burger-form{
        max-width: 400px;
        margin: 0 auto;
    }
    .input-container{
        display: flex;
        flex-direction: column;
         align-items: start;
         margin-bottom: 20px;
    }
    label{
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: solid 4px #fcba03;
    }
    input, select{
        padding: 5px 10px;
        width: 300px;
    }
    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }
    #opcionais-title{
        width: 100%;
        text-align: start;
    }
    .checkbox-container{
        display: flex;
        align-items: center;
        width: 50%;
        margin-bottom: 20px;
    }
    .checkbox-container span, 
    .checkbox-container input{
        width: auto;
}
.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}
.submit-btn{
    background-color: #222;
    color: #fcba03;
    font-weight: bold;
    border: solid 2px #222;
    padding: 10px;
    cursor: pointer;
    transition: .5s;
}
.submit-btn:hover{
    background-color: transparent;
    color: #222
}
</style>