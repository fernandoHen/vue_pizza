<template>
    <Message :msg="msg" v-show="msg" />
    <div id="order-pizza-table">
        <div>
            <div id="pizza-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente:</div>
                <div>Tipo da Massa:</div>
                <div>Tipo de Borda:</div>
                <div>Sabores</div>
                <div>Ações</div>
            </div>
        </div>

        <div id="pizza-table-rows">
            <div class="pizza-table-row" v-for="pizza in pizzas" :key="pizza.id">
                <div class="order-number">{{pizza.id}}</div>
                <div>{{ pizza.name }}</div>
                <div>{{ pizza.massa }}</div>
                <div>{{ pizza.borda }}</div>

                <div>
                    <ul>
                        <li v-for="(sabor, index) in pizza.sabores" :key="index">{{ sabor }}</li>
                    </ul>
                </div>

                <div class="action">
                    <select name="status" class="status" @change="updetePizza($event, pizza.id)">
                        <option value="">Status</option>
                        <option v-for="st in status" :key="st.id" :value="st.tipo" :selected="pizza.status == st.tipo">
                            {{ st.tipo }}
                        </option>
                    </select>
                    <button class="delete-btn" @click="deletePizza(pizza.id)">Cancelar</button>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import Message from "./Message.vue";

export default {
    
    name: "Dashboard",
    data() {
        return {
            pizzas: null,
            pizzas_id: null,
            status: [],
            msg: null
        }
    },
    components: {
        Message
    },
    methods: {
        //pega os valores do bd
        async getPedidos() {
            const req_bd = await fetch("http://localhost:8083/pizzas");
            const data = await req_bd.json(); //transforma a requisicao em json

            this.pizzas = data;
            
            //resgate do status   
            this.getStatus();
        },
        async getStatus() {
            const req_bd_status = await fetch("http://localhost:8083/status");
            const data = await req_bd_status.json();
            this.status = data;
            console.log(data);
        },
        async deletePizza(id) {
            const req_bd_delete = await fetch(`http://localhost:8083/pizzas/${id}`, {
                method: "DELETE"
            });

            const respostaDelete = req_bd_delete.json();
            this.msg = "Pedido Cancelado com Sucesso!"

            this.getPedidos(); // requisicao a menos no backend, nesse caso é aceitavel
            setTimeout(() => this.msg = "", 5000);

        },
        async updetePizza(event, id) {
            //update leva o evento e o id da pizza a ser atualizada
            const option = event.target.value;
            const dataJson = JSON.stringify({ status: option }) // converte valores de js para uma String JSON.

            //vai ate no bd_json, encontra o id e faz a alteracao do status
            const requestUpdate = await fetch(`http://localhost:8083/pizzas/${id}`, {
                method: "PATCH", //atualiza apenas o que foi enviado, o caso o status
                headers: { "Content-Type": "application/json"},
                body: dataJson
            });

            const respostaUpdate = requestUpdate.json();
            console.log(respostaUpdate)
        }
    },
    mounted() {
        this.getPedidos();
    }
}
</script>

<style scoped>
    #order-pizza-table {
        max-width: 1200px;
        margin: 0px auto; /*centralizar div na tela*/
    }

    #pizza-table-heading,
    #pizza-table-rows,
    .pizza-table-row {
        display: flex;
        flex-wrap: wrap;
    }

    #order-pizza-table {
        height: 80%;
        background-color: #5694B9;
        overflow: auto;
    }

    #pizza-table-heading {
        font-weight: bold;
        padding: 12px;
        border-bottom: 2px solid #333;
    }
    
    #pizza-table-heading div,
    .pizza-table-row div {
        width: 19%;
    }

    .pizza-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 2px solid #CCC;

    }

    #pizza-table-heading .order-id,
    .pizza-table-row .order-number {
        width: 5%;
    }
    
    select {
        padding: 12px 6px;
        margin-right: 12px;
        border-radius: 8px;
    }

    .delete-btn {
        background-color: #f9f2f4;
        border: 2px solid #FBB7B4;
        color: #D46760;
        padding: 10px;
        font-weight: bold;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        border-radius: 8px;
    }

    .delete-btn:hover {
        background-color: #D46760;
        border: 2px solid #FBB7B4;
        color: #f9f2f4;
        font-weight: bold;
    }

    .status {
        text-align: center;
        float: left;
    }

</style>