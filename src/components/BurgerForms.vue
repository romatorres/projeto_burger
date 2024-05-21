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
                <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
            </select>
        </div>
        <div class="input-container">
            <label for="carne">Escolha a carne</label>
            <select name="carne" id="carne" v-model="carne">
                <option value="">Selecione a carne</option>
                <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
            </select>
        </div>
        <div class="input-container" id="opcionais-container">
            <label id="opcionais-title" for="opcionais">Escolha os opcionais</label>
            <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                <input type="checkbox" name="opcionais" :value="opcional.tipo" v-model="opcionais">
                <span>{{ opcional.tipo }}</span>
            </div> 
        </div>
        <div class="input-container">
            <input type="submit" value="Criar seu Burger" class="submit-btn">
        </div>
    </form>
</template>

<script>
export default {
    nome: 'BurgerForms',
    data(){
        return{
        paes: null,
        carnes: null,
        opcionaisdata: null,
        nome: null,
        pao: null,
        carne: null,
        opcionais: [],
        status: 'Solicitado',
        msg: 'null'
    }
  },
   methods:{
        async getIgredientes(){
            const req = await fetch("http://localhost:3000/ingredientes")
            const data = await req.json()

            this.paes = data.paes
            this.carnes = data.carnes
            this.opcionaisdata = data.opcionais
        }
        
   },
   mounted(){
    this.getIgredientes()
   }
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