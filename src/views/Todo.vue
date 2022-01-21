<template>
<div class="home ">


<!-- Textfield de agregar tareas  start-->
<v-text-field
   v-model="newtasktitle"
   @click:append="addTask"
   @keyup.enter="addTask"
   class="pa-3"
   outlined
   label="Add Task"
   append-icon="mdi-plus"
   hide-details
   clearable
  >
  
  </v-text-field>
<!-- Textfield de agregar tareas  end-->


<v-list
class="pt=0"
      flat
    >


          <!-- Nos brinda la identificacion de los id seleccionados -->

      <div
     
      v-for="task in tasks"
        :key="task.id"
      
      >
      <!-- con un click nos brinda la linea en la tarea -->
      <!-- //y junton con la clase le damos estilo -->
        <v-list-item
        @click="doneTask(task.id)"
        :class="{'green lighten-3': task.done}"
        >
          <template v-slot:default="{ active, }">
            <v-list-item-action>
              <v-checkbox
                :input-value="active"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
              :class="{'text-decoration-line-through': task.done}"
              >
              {{task.title}}
              </v-list-item-title>
            </v-list-item-content>

        <v-list-item-action>
          <v-btn
          @click.stop="deleteTask(task.id)" 
          icon
          
          >
            <v-icon color="red lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
</v-list>
</div>

</template>

<script>

  export default {
    name: 'Home',
    data(){
      return {
        newtasktitle:'',
        tasks:[
          // {
          //   id:1,
          //   title:'Run',
          //   done:false
          // },
          // {
          //   id:2,
          //   title:'Wake up',
          //   done:false
          // },
          // {
          //   id:3,
          //   title:'Drive in F1',
          //   done:false
          // }
        ]
      }
    },
    // Metodos que usamos para un tipo CRUD
    methods:{
      doneTask(id){
        let task= this.tasks.filter(task => task.id === id)[0]
        task.done=!task.done
      },
      // metodo de eliminar tarea

      deleteTask(id){
        this.tasks = this.tasks.filter(task => task.id !== id)
      },
      // metodo de agregar tareas

      addTask(){
      let newTask={
        id:Date.now(),
        title:this.newtasktitle,
        done:false
      }
      

      this.tasks.push(newTask)
      // Despues que el textfield ingrese el parametro se limpie
      this.newtasktitle=''
      }
    }
   
  }
</script>
