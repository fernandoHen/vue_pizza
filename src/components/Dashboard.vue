<template>
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

                <div>
                    <select name="status" class="status">
                        <option value="">Status</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>
        </div>

    </div>
</template>

<script>

export default {
    name: "Dashboard",
    data() {
        return {
            pizzas: null,
            pizzas_id: null,
            status: []
        }
    },
    methods: {
        //pega os valores do bd
        async getPedidos() {
            const req_bd = await fetch("http://localhost:8083/pizzas");
            const data = await req_bd.json(); //transforma a requisicao em json

            this.pizzas = data;
            
            //resgate do status   

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
    }

    .delete-btn:hover {
        background-color: #D46760;
        border: 2px solid #FBB7B4;
        color: #f9f2f4;
        font-weight: bold;
    }
</style>