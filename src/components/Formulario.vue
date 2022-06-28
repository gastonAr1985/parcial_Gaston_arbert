<template >

  <section class="tp-4-componentes-formulario">
    <h1>FORMULARIO</h1>

     <div class="jumbotron">
    
        <vue-form :state="formState" @submit.prevent="enviar()">
 
        <validate tag="div">
        <label for="nombre">Nombre</label>
        <input 
        type="text"
        id="nombre"
        class="form-control"
        autocomplete="off" 
        v-model.trim="campos.nombre" 
        required 
        name="nombre" 
        :minlength="caracteresMinimos"
        :maxlength="caracteresMaximos"
        
        />
 
        <field-messages name="nombre" show="$dirty">
        <div slot="required" class="alert alert-danger mt-1" >El nombre es requerido</div>
        <div slot="minlength" class="alert alert-danger mt-1" >Son requeridos {{caracteresMinimos}} caracteres</div>
        <div slot="no-espacios" class="alert alert-danger mt-1">Hay espacios</div>
        </field-messages>
        </validate>
       <br>

       <validate tag="div">
        <label for="apellido">Apellido</label>
        <input 
        type="text"
        id="apellido"
        class="form-control"
        autocomplete="off" 
        v-model.trim="campos.apellido" 
        required 
        name="apellido" 
        :minlength="caracteresMinimos"
        :maxlength="caracteresMaximos"
        
        />
 
        <field-messages name="apellido" show="$dirty">
        <div slot="required" class="alert alert-danger mt-1" >El Apellido es requerido</div>
        <div slot="minlength" class="alert alert-danger mt-1" >Son requeridos {{caracteresMinimos}} caracteres</div>
        <div slot="no-espacios" class="alert alert-danger mt-1">Hay espacios</div>
        </field-messages>
        </validate>
       <br>

        <validate tag="div">
        <label for="edad">edad</label>
        <input 
        type="number"
        id="edad"
        class="form-control"
        autocomplete="off" 
        v-model.number="campos.edad" 
        required 
        name="edad" 
        :min="edadMinima"
        :max="edadMaxima"
        />
  
        <field-messages name="edad" show="$dirty">
          <div slot="required" class="alert alert-danger mt-1" >La edad es requerida</div>
          <div slot="min" class="alert alert-danger mt-1" >edad mininma {{edadMinima}} </div>
          <div slot="max" class="alert alert-danger mt-1" >edad maxima {{edadMaxima}} </div>
        </field-messages>
      </validate>

        <br>

    

       <validate tag="div">
        <label for="email">Email</label>
        <input 
        type="email"
        id="email"
        class="form-control"
        autocomplete="off" 
        v-model.trim="campos.email" 
        required 
        name="email" 
    
        />
  
        <field-messages name="email" show="$dirty">
        <div slot="required" class="alert alert-danger mt-1" >Email es requerido</div>
        <div slot="email" class="alert alert-danger mt-1" >Email no valido</div>
        </field-messages>
        </validate>

        <br>
               <validate tag="div">
        <label for="nota">Nota</label>
        <input 
        type="number"
        id="nota"
        class="form-control"
        autocomplete="off" 
        v-model.number="campos.nota" 
        required 
        name="nota" 
        :min="notaMin"
        :max="notaMax"
        />
  
        <field-messages name="edad" show="$dirty">
          <div slot="required" class="alert alert-danger mt-1" >La nota es requerida</div>
          <div slot="min" class="alert alert-danger mt-1" >nota mininma {{notaMin}} </div>
          <div slot="max" class="alert alert-danger mt-1" >nota maxima {{notaMax}} </div>
        </field-messages>
      </validate>

        <br>
    
 
        <button type="submit " class="btn btn-success my-5" :disabled="formState.$invalid">Enviar</button>

            <div v-if="usuarios.length">
                <div class="table-responsive">
                    <table   class="table table-dark">
                        <tr>
                          
                            <th>Nombre</th>
                            <th>Edad</th>
                            <th>Nota</th>
                        </tr>  
                            
                        
                        <tr v-for="(usuario,index) in usuarios" :key="index">
                            <td>{{ usuario.nombre }}</td>
                            <td>{{ usuario.edad }}</td>
                            <td>{{ usuario.nota }}</td>
                      
                        </tr> 
                    </table> 
              </div>
            
      </div> 
  </vue-form>
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
        formState:{},
        campos: this.obtenerCampos(),
        caracteresMinimos: 5,
        caracteresMaximos: 15,
        edadMinima:18,
        edadMaxima:120,
        usuarios:[],
        notaMin:0,
        notaMax:10


      }
    },
    methods: {
      obtenerCampos(){
        return {
          nombre: '',
          apellido:'',
          edad:'',
          email:'',
          nota:''
      }
      },

      enviar(){

        this.usuarios.push(this.campos)
        this.campos = this.obtenerCampos()
        this.formState._reset()

      }

    },
    computed: {

    }
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