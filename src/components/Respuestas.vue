<template >

  <section class="src-components-respuestas">
    <div class="jumbotron">

    <h1>Respuestas</h1>
    <div v-if="respuestas.length" class="table-responsive">
      <table class="table table-dark">
        <tr>
          
          <th>Pregunta Numero</th>
          <th>Respuesta</th>

        </tr>
        <tr v-for="(respuesta,index) in respuestas" :key="index">

          <th>{{respuesta.pregunta}}</th>
          <th>{{respuesta.respuesta}}</th>

        </tr>
      </table>
    </div>
    </div>
  </section>

</template>

<script >

  export default  {
    name: 'src-components-respuestas',
    props: [],
    mounted () {

    },
    data () {
      return {

        respuestas:[
          {pregunta: 1, respuesta: 'A'},
          {pregunta: 2, respuesta: 'A'},

        ]

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-respuestas {

  }
</style>
