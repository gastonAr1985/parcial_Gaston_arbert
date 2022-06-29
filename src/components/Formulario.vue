<template >

  <section class="tp-4-componentes-formulario">
    <h1>Ingresar Textos</h1>

     <div class="jumbotron">
    
       
 
        <label for="text">Ingrese texto</label>
        <input 
        type="text"
        id="text"
        class="form-control"
        v-model="texto" 
        name="tex" >
        

           
 
     <div v-if="texto">

      <p> Cantidad caracteres {{contar}}</p>
      
      <p>{{pasarMin(texto)}}</p>
      
      <p>{{pasarMay(texto)}}</p>
      

     <!--  <p>{{codificar(texto)}}</p> -->
     </div>
     </div>


      
  </section>

  

</template>

<script lang="js">

  export default  {
    name: 'tp-4-componentes-formulario',
    props: [],
    mounted () {

    },
    data () {
      return {
       
        texto:''
       


      }
    },
    methods: {
      
      pasarMin(text){
        return text.toLowerCase()
      },

      pasarMay(text){
        return text.toUpperCase()
      },

/*       codificar(tex){
        let texto = tex.toLowerCase()
        let texto1 = texto.split('')
        let tex=[]
        
       
       for (let i = 0; i < texto1.length; i++){
            if(texto1[i] =='a')this.text[i] = 'u'
            else if(texto1[i] == 'e')this.text1[i] = 'o'
            
            else if(texto1[i] == 'o')this.text[i] = 'e'
           
            else if(texto1[i] == 'u'){this.text[i] = 'a'

           
          }
           
         console.log('codificar',text )
        return texto1
      } */

      
     


    },
    computed: {
      contar(){
        let cant = this.texto.length
        return cant
      }
        
     
      },
        

    }
  
</script>

<style scoped lang="css">
  .tp-4-componentes-formulario {

  }
   .jumbotron {
    background-color: purple;
    color:white;
  }
  hr{
    background-color: #bbb;
  }
</style>