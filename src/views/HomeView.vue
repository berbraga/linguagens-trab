<template>
  <div class="container">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <input id="input" placeholder="digite o codigo aqui: " class="Input">
    <div class="boxButton">
      <button @click=" this.bernardo() ">Limpa</button>
      <button @click=" this.bernardo() ">Analizar</button>
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
      VALID: 'sentença válida:',
      aritimetic:  'operador aritmético',
      sentencaInvalida: 'ERRO => sentença inválida',
      simbuloInvalido: 'ERRO => símbolo(s) inválido(s)',
      aritimeticOperators: ['+','-','/','*'],
      endSentence: ['$','+','-','/','*'],

    };
  },
  methods:{
    bernardo:function(){
      console.clear();
      const token = document.getElementById('input').value
      const results = document.getElementById('results')
      

      
      let retornos = [];
      let sentencas = ''
      for (let i = 0; i < token.length; i++) {

        if(!this.endSentence.includes(token.charAt(i))){
          const char = token[i];
          console.log('no if',i, char,)
          sentencas +=  char;

        }else{
          console.log(sentencas)
          retornos.push(sentencas);
          sentencas = ''; 
          console.log(token[i])
        
        }
        
      }
      console.log(retornos)








      // results.value += token
    }
  }

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