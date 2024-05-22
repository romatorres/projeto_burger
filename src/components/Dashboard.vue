<template>
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
                        <select>
                            <option value="confirmado">Confirmado</option>
                        </select>
                        <button class="btn-table">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "Dashboard",
    data(){
        return{
            burgers: null,
            burger_id: null,
            status: []
        }
    },
    methods:{
        async getPedidos(){
            const req = await fetch('http://localhost:3000/burgers')

            const data = await req.json()

            this.burgers = data
        }
    },
    mounted(){
        this.getPedidos()
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
  padding: 8px 60px;
}
.btn-table{
    background-color: #222;
    color: #fcba03;
    font-weight: bold;
    border: solid 2px #222;
    padding: 8px 30px;
    cursor: pointer;
    transition: .5s;
}
.btn-table:hover{
    background-color: transparent;
    color: #222
}
select{
    padding: 8px 10px;
    margin-right: 10px;
}
</style>