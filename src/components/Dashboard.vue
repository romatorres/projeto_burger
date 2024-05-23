<template>
    <Message :msg="msg" v-show="msg" />
    <div class="table-container">
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Pão</th>
                    <th>Carne</th>
                    <th>Opcionais</th>
                    <th>Ações</th>
                </tr>
            </thead>
            <tbody v-for="burger in burgers" :key="burger.id">
                <tr>
                    <td>{{ burger.id }}</td>
                    <td>{{ burger.nome }}</td>
                    <td>{{ burger.pao }}</td>
                    <td>{{ burger.carne }}</td>
                    <td>
                        <ul v-for="(opcional, index) in burger.opcionais" :key="index">
                            <li>{{ opcional }}</li>
                        </ul>
                    </td>
                    <td>
                        <select name="status" id="status" @change="updateBurgers($event, burger.id)">
                            <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">{{ s.tipo }}</option>
                        </select>
                        <button class="btn-table" @click="deleteBurger(burger.id)">Cancelar</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import Message from './Message.vue';

export default {
    name: "Dashboard",
    data(){
        return{
            burgers: null,
            burger_id: null,
            status: [],
            msg: null
        }
    },
    methods:{
        async getPedidos(){
            const req = await fetch('http://localhost:3000/burgers')

            const data = await req.json()

            this.burgers = data

            this.getStatus()
        },
        async getStatus(){
                const req = await fetch('http://localhost:3000/status')

                const data = await req.json()

                this.status = data
            },
            async deleteBurger(id){
                const req = await fetch(`http://localhost:3000/burgers/${id}`, 
                {method: 'DELETE'})

                const res = await req.json()

                // Mensagem de confirmação
                 this.msg = `O pedido foi excluido com sucesso!`

                // Limpar menssagem
                setTimeout(() => this.msg = '', 4000)

                this.getPedidos()
            },
            async updateBurgers(event, id){
                const option = event.target.value

                const dataJson = JSON.stringify({status: option}) 

                const req = await fetch(`http://localhost:3000/burgers/${id}`, 
                {method: 'PATCH',
                headers: {'Content-Type': 'application/json'},
                body: dataJson }) 

                const res = await req.json()

                // Mensagem de confirmação
                this.msg = `O status do pedido Nº ${res.id} foi atualizado para ${res.status}!`

                // Limpar menssagem
                setTimeout(() => this.msg = '', 4000)
            }   
        },
    mounted(){
        this.getPedidos()
    },
    components: {
        Message
    }
}
</script>

<style scoped>
 .table-container {
   display: flex;
   justify-content: center;
  }
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  letter-spacing: 1px;
}
th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 40px;
}
.btn-table{
    background-color: #222;
    color: #fcba03;
    font-weight: bold;
    border: solid 2px #222;
    padding: 8px 24px;
    cursor: pointer;
    transition: .5s;
}
.btn-table:hover{
    background-color: transparent;
    color: #222
}
select{
    padding: 8px 8px;
    margin-right: 8px;
}
</style>