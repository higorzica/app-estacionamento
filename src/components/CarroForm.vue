<template>


    <div class="fundo">

            <Mensagem :msg="msg" v-show="msg" />



        <form id="carro-form" @submit="createCarro">
            <div class="container">
                <div class="container row">
                    <label for="nome">Nome da Pessoa: </label>
                    <input type="text" id="nome" v-model="nome" placeholder="Informe o seu nome: ">
                    
                    <label for="nomeCarro">Nome do Carro: </label>
                    <input type="text" id="nomeCarro" v-model="nomeCarro" placeholder="Informe o nome do Carro ">

                </div>
            </div>

            <div class="container">
                <div class="container row">
                    <label for="placaCarro">Placa do Carro: </label>
                    <input type="text" id="placaCarro" v-model="placaCarro" placeholder="Informe a placa do Carro: ">

                    <label for="hora">Horário de Entrada: </label>
                    <input type="text" id="hora" v-model="hora" placeholder="Informe o Horári de Entrada: ">
                    
                </div>
            </div>


                <div class="input-container">

                    <input type="submit" class="submit-btn" value=" Cadastrar Carro">
                    
                </div>




        </form>


    </div>



</template>

<script>

import Mensagem from './Mensagem.vue';

  export default {
    name:"CarroForm",

    data(){
        return {
                nome: null,
                nomeCarro: null,
                placaCarro: null,
                hora: null,
                msg: null
        }
    },
    methods: {
            async createCarro(e){
                e.preventDefault();
                // console.log("Carro cadastrado com Sucesso");
                const data = {
                    nome: this.nome,
                    nomeCarro: this.nomeCarro,
                    placaCarro: this.placaCarro,
                    hora: this.hora,
                    status: "Solicitado",
                }
                // console.log(data);
                const dataJson = JSON.stringify(data);
                // Fazendo um POST
                const req = await fetch("http://localhost:3000/carros", {
                    method: "POST",
                    headers: { "Content-Type" : "application/json"},
                    body: dataJson
                });
                const res = await req.json();
                console.log(res);

           //  Mensagem de cadastro de carro
            this.msg = `Carro cadastrado com Sucesso!`;
            // Limpar a Mensagem após um tempo
            setTimeout(() => this.msg = "", 3000)
                // Limpara campos
                this.nome = "";
                this.nomeCarro = "";
                this.placaCarro = "";
                this.hora = "";
            }
        },
        components: {
            Mensagem
        }
    }
</script>


<style scoped>
    #carro-form {
        max-width: 80%;
        margin: 0 auto;
    }
    .container {
        margin-top: 25px;
        margin-bottom: 15px;
    }
    .container row{
        display: flex;
        flex-direction: row;
        justify-content:center;
        margin-top: 15px;
        margin: 0 auto;
    }
    label {
        margin-left: 15px;
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 3px solid #3F7FBF;
    }
    input {
        padding: 5px 20px;
        width: 300px;
    }
    .submit-btn {
        background-color: #3F7FBF;
        color: white;
        font-weight:  bold;
        padding: 10px;
        font-size: 16px;
        border: 2px solid white;
        cursor: pointer;
        transition:  .5s;
        margin: 15px;
    }
    .submit-btn:hover {
        background-color: #00366d;
        font-size: 17px;
        color: rgb(1, 250, 1);
    }
    .fundo{
        padding-top: 15px;
        background-color: rgb(201, 201, 201);
    }
</style>