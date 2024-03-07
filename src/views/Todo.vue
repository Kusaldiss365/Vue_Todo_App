<template>
  <div class="home">
    <v-text-field
            v-model="newTaskTitle"
            @click:append="addTask"
            @keyup.enter="addTask"
            class="pa-6"
            append-icon="mdi-plus"
            label="Add Task"
            variant="outlined"
            hide-details
            clearable
          ></v-text-field>

    <v-list lines="two" select-strategy="classic" class="pt-0">
        <div v-for="task in tasks" :key=task.id>
          <v-list-item @click="doneTask(task.id)">
          <template v-slot:prepend>
            <v-list-item-action>
              <v-checkbox-btn :model-value="task.done"></v-checkbox-btn>
            </v-list-item-action>
          </template>

          <v-list-item-content>
            <v-list-item-title :class="{ 'text-decoration-line-through': task.done }">
              {{ task.title }}
            </v-list-item-title>
          </v-list-item-content>

          <template v-slot:append>
            <v-btn color="grey-lighten-1" icon="mdi-delete" variant="text" @click.stop="deleteTask(task.id)"></v-btn>
          </template>
        </v-list-item>

        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
import { defineComponent } from 'vue';


export default defineComponent({
  name: 'HomeView',
  data() {
    return{
      newTaskTitle: '',
          tasks: [
        { 
          id: 1,
          title: "Wake up",
          done: false,
        },
        {
          id: 2,
          title: "Get Apples",
          done: false,
        },
        {
          id: 3,
          title: "Eat Apples",
          done: false,
        }
      ]
  }
  },
  components: {},
  methods: {
    addTask(){
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false,
      }
      this.tasks.push(newTask)
    },
    doneTask(id){
      let task = this.tasks.filter(task=> task.id === id)[0]
      task.done = !task.done
    },
    deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }
});
</script>
