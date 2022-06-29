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
      

      <p>{{codificar(texto)}}</p>

      <p>{{minMay(texto)}}</p>

      <p>{{mayMin(texto)}}</p>
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

       codificar(tex){
        let texto = tex.toLowerCase()
        let texto1 = texto.split('')
        let text1=[]
        let u ='u'
        let o = 'o'
        let e = 'e'
        let a = 'a'
            
            for (let i = 0; i < texto1.length; i++){
            if(texto1[i] == a){
              console.log(texto1[i])
              text1.push(u)
              }else if(texto1[i] === e){
              text1.push(o)
              }else if(texto1[i] === o){
                text1.push(e)
              }else if(texto1[i] === u){
                text1.push(a)
              }else{
                text1.push(texto1[i])
              }
            }
         console.log('codificar' )
        return text1.join('')
            
       },

       mayMin(tex){
        let texto = tex.toLowerCase()
        let texto1 = texto.split('')
        let texMayMin=[]
        for (let i = 0; i < texto1.length; i++){
           if(i%2==0){
            texMayMin.push(texto1[i].toUpperCase().split())
           }else{
             texMayMin.push(texto1[i].toLowerCase().split())
           }
        }
          return texMayMin.join('')
       },
       
        minMay(tex){
        let texto = tex.toLowerCase()
        let texto1 = texto.split('')
        let texMayMin=[]
        for (let i = 0; i < texto1.length; i++){
           if(i%2!=0){
            texMayMin.push(texto1[i].toUpperCase().split())
           }else{
             texMayMin.push(texto1[i].toLowerCase().split())
           }
        }
          return texMayMin.join('')
       }
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