<template>
    <div>
        <Message :msg="msg" v-show="msg" />
        <div>
            <form id="pizza-form" @submit="createPizza">
                <div class="input-container">
                    <label for="nameClient">Nome do Cliente:</label>
                    <input type="text" id="name" name="name_id" class="text" v-model="name" placeholder="Digite o seu nome" />
                </div>
                
                <div class="input-container">
                    <label for="massa">Escolha a Massa</label>
                    <select name="massa" id="massa_id" v-model="massa">
                        <option class="text" value="" disabled selected>Selecione o tipo de massa</option>
                        <option class="text" v-for="massa in massas" :key="massa.id" :value="massa.tipo">{{massa.tipo}}</option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="borda">Escolha a Borda</label>
                    <select name="borda" id="borda_id" v-model="borda" value="">
                        <option class="text" value="" disabled selected>Selecione recheio da borda</option>
                        <option class="text" v-for="borda in bordas" :key="borda.id" :value="borda.tipo">{{borda.tipo}}</option>
                    </select>
                </div>

                <div id="mass-container" class="input-container">
                    <label for="sabores">Escolha o sabor da Pizza</label>
                    <div id="sabor-title" class="checkbox-container" v-for="saborData in saboresData" :key="saborData.id">
                        <input type="checkbox" name="sabores_name" v-model="sabores" :value="saborData.tipo">
                        <span>{{saborData.tipo}}</span>
                    </div>
                </div>

                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Fazer pedido">
                </div>

            </form>
        </div>
    </div>
</template>


<script>
import Message from "./Message.vue";

export default {
    name: "PizzaForm",
    //relacionamento com o banco de dados   
    data() {
        return {
//OBS: ESTA SENDO FEITO DESSA MANEIRA E NAO NO BACKEND, PELO FATO DE NAO TER UM
//BACKEND FEITO (AINDA NAO TEM)

            //dados que vem do servidor - inicio
            massas: null,
            bordas: null,
            saboresData: null,
            // dados que vem para preencher o form - fim

            //dados que vao ser enviados ao bd - inicio
            name: null,
            massa: null,
            borda: null,
            sabores: [],
            msg: null
            //dados que vao ser enviados ao bd - fim
        }
    },
    methods: {
        //trabalha com o backend para trazer os ingredientes - metodo para pegar ingredientes

        async getIngredientes() {
            //crio a chamada do backend, nesse caso url que da acesso a api
            const reqBackend = await fetch("http://localhost:8083/ingredientes");
            const data = await reqBackend.json(); // espera a requisicao para ter os dados em json

            this.massas = data.massas;
            this.bordas = data.bordas;
            this.saboresData = data.sabores;

        },

        //metodo para enviar os dados do formulario para o backend em post
        //e -> argumente de evento, isso para parar o evento do formulario quando clicar
        //no submit
        async createPizza(e) {
            e.preventDefault();
            //cria um objeto com os dados que foram preenchidos
            const data = {
                name: this.name,
                massa: this.massa,
                borda: this.borda,
                sabores: Array.from(this.sabores),
                status: "Solicitado"
            }   

            //comunicacao via request para o servidor
            const dataJson = JSON.stringify(data)//pega o objeto json e transforma em um texto
            
            //envio ima requisicao para a api de pizzas para integrar com o bd
            const reqBackendAdd = await fetch("http://localhost:8083/pizzas", {
                //parametros
                method: "POST",
                headers: {"Content-Type": "application/json"}, //digo que estou se comunicando com um json
                body: dataJson //corpo da requisicao para enviae os dadosjson como texto
            });

            //resposta da requisicao
            const resposta_reqBackendAdd = await reqBackendAdd.json();
            console.log(resposta_reqBackendAdd);

            //adiciona msg do sistema
            this.msg = `Pedido Número: ${resposta_reqBackendAdd.id} realizado com sucesso!`

            //limpar msg
            setTimeout(() => this.msg = "", 5000);

            //limpar os campos
            this.name = "";
            this.massa = "";
            this.borda = "";
            this.sabores = "";
            
        }
    },
    //quando montar o componente 
    mounted() {
        this.getIngredientes(); 
    },
    components: {
        Message
    }
}
</script>


<style scoped>
    #pizza-form {
        max-width: 400px;
        margin: 0 auto;
    }

    .input-container {
        display: flex;
        flex-direction: column; /*lable fica em uma linha e o input na outra*/
        margin-bottom: 15px;
    }

    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #222;
    }

    input, select {
        padding: 5px 10px; /*interno*/
    }

    #mass-container {
        flex-direction: row;
        flex-wrap: wrap;
    }

    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .main-container {
        overflow-y: scroll;
    }

    .checkbox-container input,
    .checkbox-container span {
        width: auto;
    }

    .checkbox-container span {
        margin-left: 6px;
        font-weight: bold;
    }

    .submit-btn {
        background-color: #222;
        color: bisque;
        font-weight: bold;
        border: 2px solid rgb(114, 114, 114);
        height: 50px;
        font-size: 16px;
        cursor: pointer;
    }

    .submit-btn:hover{
        opacity: 0.8;
    }

    .text {
        font-family: Helvetica;
        font-size: 18px;
    }

</style>