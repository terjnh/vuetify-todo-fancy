<template>
  <div class="home pa-0">
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

<!-- @click.stop enables the 'delete' button to NOT trigger task.done -->
            <v-list-item-action
            @click.stop="deleteTask(task.id)"
            >
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
      tasks: [
        {
          id: 1,
          title: 'Wake up',
          done: false
        },
        {
          id: 2,
          title: 'Get bananas',
          done: false
        },
        {
          id: 3,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 4,
          title: 'Wake up',
          done: false
        },
        {
          id: 5,
          title: 'Get bananas',
          done: false
        },
        {
          id: 6,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 7,
          title: 'Wake up',
          done: false
        },
        {
          id: 8,
          title: 'Get bananas',
          done: false
        },
        {
          id: 9,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 10,
          title: 'Wake up',
          done: false
        },
        {
          id: 11,
          title: 'Get bananas',
          done: false
        },
        {
          id: 12,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 13,
          title: 'Wake up',
          done: false
        },
        {
          id: 14,
          title: 'Get bananas',
          done: false
        },
        {
          id: 15,
          title: 'Eat bananas',
          done: false
        },
                {
          id: 16,
          title: 'Wake up',
          done: false
        },
        {
          id: 17,
          title: 'Get bananas',
          done: false
        },
        {
          id: 18,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 19,
          title: 'Wake up',
          done: false
        },
        {
          id: 20,
          title: 'Get bananas',
          done: false
        },
        {
          id: 21,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 22,
          title: 'Wake up',
          done: false
        },
        {
          id: 23,
          title: 'Get bananas',
          done: false
        },
        {
          id: 24,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 25,
          title: 'Wake up',
          done: false
        },
        {
          id: 26,
          title: 'Get bananas',
          done: false
        },
        {
          id: 27,
          title: 'Eat bananas',
          done: false
        },
        {
          id: 28,
          title: 'Wake up',
          done: false
        },
        {
          id: 29,
          title: 'Get bananas',
          done: false
        },
        {
          id: 30,
          title: 'Eat bananas',
          done: false
        }
      ],
    }
  },
  methods: {
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
