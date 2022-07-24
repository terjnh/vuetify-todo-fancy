<template>
  <div class="home pa-0">

    <v-text-field class="pa-3" v-model="newTaskTitle" outlined label="Add Task" append-icon="mdi-plus" hide-details
      clearable
      @click:append="addTask"
      @keyup:enter="addTask"
      >
    </v-text-field>

    <v-list class="pt-0" flat subheader>
      <v-subheader>List of ToDo items:</v-subheader>
      <div v-for="task in tasks" :key="task.id">
        <v-list-item @click="doneTask(task.id)" :class="{ 'blue lighten-5': task.done }">
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title :class="{ 'text-decoration-line-through': task.done }">{{ task.title }}
              </v-list-item-title>
            </v-list-item-content>

            <h5 class="black--text font-italic font-weight-regular mb-0">{{task.datetime}}</h5>

            <!-- @click.stop enables the 'delete' button to NOT trigger task.done -->
            <v-list-item-action @click.stop="deleteTask(task.id)">
              <v-btn icon>
                <v-icon color="primary">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider inset></v-divider>
      </div>

    </v-list>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      newTaskTitle: '',
      tasks: [
        {
          id: 1658635212987,
          title: 'Wake up',
          done: false,
          datetime: "24/07/2022, 12:08:39"
        },
        {
          id: 1658635212988,
          title: 'Get bananas',
          done: false,
          datetime: "24/07/2022, 12:08:39"
        },
        {
          id: 1658635212989,
          title: 'Eat bananas',
          done: false,
          datetime: "24/07/2022, 12:08:39"
        },
        {
          id: 1658635212990,
          title: 'Wake up',
          done: false,
          datetime: "24/07/2022, 12:08:39"
        },
        {
          id: 1658635212995,
          title: 'Get bananas',
          done: false,
          datetime: "24/07/2022, 12:08:39"
        }
      ],
    }
  },
  methods: {
    addTask() {
      console.log('AddTask')
      var dateNow = new Date()
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false,
        datetime: dateNow.toLocaleString()
      }
      this.tasks.push(newTask)
      this.newTaskTitle = ''
      console.log("tasks:", this.tasks)
    },
    doneTask(id) {
      let task = this.tasks.filter(task => task.id === id)[0]
      task.done = !task.done
      console.log("TaskTitle:", task.title, "| status: ", task.done)

    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }
}
</script>
