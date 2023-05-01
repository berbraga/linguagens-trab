<template>
  <div class="container">
    <input id="input" placeholder="digite o codigo aqui: " class="Input">
    <div class="boxButton">
      <button @click=" this.clear() ">Limpar</button>
      <button @click=" this.main() ">Analizar</button>
    </div>
    <textarea name="results" id="results" ></textarea>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import {updateExpressionWithTypeArguments} from 'typescript'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data(){
    return{
      alfabeto: ['a','b','c','d','e'],
      VALID: 'sentença válida:',
      aritimetic:  'operador aritmético',
      sentencaInvalida: 'ERRO => sentença inválida',
      simbuloInvalido: 'ERRO => símbolo(s) inválido(s)',
      aritimeticOperators: ['+','-','/','*'],
      endSentence: ['$','+','-','/','*'],
      tabelaT:[
        [ 11, 11,  6,  9, 11, 11],
        [ 11, 11, 11,  9, 11, 11 ],
        [  3, 11,  0,  7, 11, 11 ],
        [ 11,  4, 11, 11, 11, 11 ],
        [  5, 11, 11, 11, 11, 11 ],
        [ 11,  2, 11, 11, 11, 11 ],
        [ 11, 11,  0,  7, 11, 11 ],
        [ 11, 11, 11, 11,  1, 11 ],
        [ 11, 11, 11,  7, 11, 11 ],
        [ 11, 11, 11, 11,  8, 11 ],
        [ 11, 11, 11, 11, 11, 11 ],
      ],
      EF: [1,1,0,0,0,0,0,0,0,0,0],


    };
  },
  methods:{
    getSentencas: function (token){

      let sentencas = [];
      let sentenca = '';
      for (let i = 0; i < token.length; i++) {
        if(!this.endSentence.includes(token.charAt(i))){
          sentenca +=  token[i];
        }else{
          sentenca +=  token[i];
          sentenca+= '$';
          sentencas.push(sentenca);
          sentenca = ''; 
        }
      }
      return sentencas;
    },
    inAlfhabeth: function(sentenca){
          
      for(let i = 0; i < sentenca.length - 1 ; i++  ){
        if (!this.alfabeto.includes(sentenca[i])) {
          // resposta = `Sentenca Invalida - Simbulo Invalido: ${sentenca}`
          return false;
        }
      }
      return true;
      
    },

    main:function(){
      console.clear();
      console.log(this.tabelaT[2][3])
      const input = document.getElementById('input');
      const results = document.getElementById('results');
      let toke = input.value;
      
      const token = toke + "$";
      const sentencas = this.getSentencas(token);
      console.log(sentencas);
      
      for (let i = 0 ; i < sentencas.length ; i++) {
        if(!this.inAlfhabeth(sentencas[i])){
          results.value += `ERRO - Simbulo Invalido: ${sentencas[i]}\n`
        }




      }

    
      // console.log(retornos)

      // results.value += token
    },
    clear:function(){
      document.getElementById('input').value = '';
      document.getElementById('results').value = '';
    },
  },

}
</script>

<style scoped>

.container{
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  align-content: center;
  align-items: center;
  justify-content: center;
}

.boxButton{

}

#results {
  width: 100%;
  min-height: 400px ;
  background-color: rgb(251, 218, 175);
  margin-top: 10px;
}
.Input{
  width: 400px;
  height: 50px;
  border-radius: 20px;
  border: 2px solid rgb(68, 48, 48);
  font: rgb(0, 0, 0) ;
  background-color: rgb(251, 218, 175);
  margin-bottom: 10px;
}

</style>