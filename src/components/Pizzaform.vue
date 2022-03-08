<template>
    <div>
        <p>Componente de mensagem</p>
        <div>
            <form id="pizza-form">
                <div class="input-container">
                    <label for="nameClient">Nome do Cliente:</label>
                    <input type="text" id="name" name="name" v-model="name" placeholder="Digite o seu nome" />
                </div>
                
                <div class="input-container">
                    <label for="mass">Escolha a Massa</label>
                    <select name="mass" id="mass" v-model="mass">
                        <option value="">Selecione o tipo de massa</option>
                        <option value="teste">teste</option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="masedges">Escolha a Borda</label>
                    <select name="edge" id="edge" v-model="edge">
                        <option value="">Selecione recheio da borda</option>
                        <option value="teste">borda</option>
                    </select>
                </div>

                <div id="mass-container" class="input-container">
                    <label for="mass">Escolha o sabor da Pizza</label>
                    <div id="mass-title" class="checkbox-container">
                        <input type="checkbox" name="mass" v-model="mass" value="frango">
                        <span>Frango</span>
                    </div>
                    <div id="mass-title" class="checkbox-container">
                        <input type="checkbox" name="mass" v-model="mass" value="frango">
                        <span>Frango</span>
                    </div>
                    <div id="mass-title" class="checkbox-container">
                        <input type="checkbox" name="mass" v-model="mass" value="frango">
                        <span>Frango</span>
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
export default {
    name: "PizzaForm",
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

</style>