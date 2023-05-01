<template>
  <div class="container">
    <input id="input" placeholder="digite o codigo aqui: " class="Input">
    <div class="boxButton">
      <button @click=" this.clear() ">Limpar</button>
      <button @click=" this.main() ">Analizar</button>
    </div>
    <textarea name="results" id="results" cols="50" rows="10"></textarea>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

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
          sentenca+= '$';
          sentencas.push(sentenca);
          sentenca = ''; 
        }
      }
      return sentencas;
    },
    main:function(){
      console.clear();
      const input = document.getElementById('input');
      const results = document.getElementById('results');
      let toke = input.value;
      
      const token = toke + "$";
      const sentencas = this.getSentencas(token);
      console.log(sentencas);
    
      // console.log(retornos)

      results.value += token
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
.Input{
  width: 400px;
  height: 50px;
  border-radius: 20px;
  border: 2px solid black;
  font: black ;
}

</style>