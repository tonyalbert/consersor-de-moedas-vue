<template>
    <div class="conversor">
        <h2> {{ moedaA }} - {{ moedaB }}</h2>
        <input class="input" type="number"  v-model="moedaA_value">
        <input class="btn" type="button" value="Converter" v-on:click="converter">
        <h2 class="resultado">{{ moedaB_value }}</h2>
    </div>
</template>


<script>

    export default {
        name: "Conversor",
        props: ["moedaA", "moedaB"],
        data(){
            return{
                moedaA_value: "",
                moedaB_value: 0 
            }
        },
        methods:{

            converter(){
                let a = this.moedaA;
                let b = this.moedaB;
                let de_para = a + "-" + b;
                let url = `https://economia.awesomeapi.com.br/json/last/${de_para}`;
                
                fetch(url)
                .then(res => {
                    return res.json();
                })
                    .then(json=>{
                        let moedas = this.moedaA + this.moedaB;
                        let cotacao = json[moedas].ask;                        
                        this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
                    })
            }   

        }
    }; 

</script>


<style scoped>

h2{
    font-size: 3.5vh;
  color: #ffffff;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-bottom: 15px;
}
.conversor{
    max-width: 45vh;
    box-shadow: -3px 4px 22px 11px rgba(0,0,0,0.17);
    background: linear-gradient(90deg, #03212b 0%, #03212b 36%, #0a303d 100%);
    border-radius: 20px;
    padding: 15px 30px;
}

.input{
    padding: 11px 20px;
  font-size: 18px;
  width: 90%;
  border-radius: 9px;
  border: none;
  outline: none;
  box-sizing: border-box;
  margin-bottom: 15px;
  border: 2px solid #00a8e8;
  transition: all 0.2s ease-in-out;
}

.input:hover{
    border-color: #007ea7;
}

.input:focus {
    border-color: #007ea7;
    box-shadow: 0px 0px 0px 2px #007ea7;
}

.btn {
  /* Estilo básico do botão */
  color: rgb(235, 238, 241);
  font-size: 18px;
  font-weight: bold;
  text-transform: uppercase;
  text-align: center;
  text-decoration: none;
  transition: all 0.2s ease-in-out;
  border: none;
  outline: none;
font-size: 2vh;
margin-bottom: 15px;
padding: 11px;
border-radius: 15px;
  background-color: #00a8e8;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.1);
}

.btn:hover {
    background-color: #007ea7;
    box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
    transform: translateY(-2px);
  }

  .resultado{
    font-size: 3.5vh;
    margin-bottom: 0;

  }

</style>