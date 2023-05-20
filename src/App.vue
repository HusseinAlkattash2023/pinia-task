<template>
  <div>

    <!-- heading -->
    <header>
      <img src="./assets/logo.svg" alt="pinia logo"/>
      <h1>Pinia Tasks</h1>
      <p>{{taskStore.name}}</p>
    </header>

    <!-- new task form-->
    <div class="new-task-form">
      <TaskForm/>
    </div>

    <!-- filter -->
    <div class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Fav tasks</button>
    </div>

    <!-- task list -->
    <div class="task-list" v-if="filter === 'all'">
      <p>Your have {{taskStore.totalCount}} tasks left to do</p>
      <div v-for="task in taskStore.tasks" :key="task">
          <TaskDetails :task="task"/>
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <p>Your have {{taskStore.favCount}} favs left to do</p>
      <div v-for="task in taskStore.favs" :key="task">
          <TaskDetails :task="task"/>
      </div>
    </div>

  </div>
</template>

<script>
import {ref} from "vue";
import {useTaskStore} from "./store/TaskStore";
import TaskDetails from "./components/TaskDetails.vue";
import TaskForm from "./components/TaskFrom.vue";

  export default {
    components:{TaskDetails , TaskForm},
    setup(){
      const taskStore = useTaskStore();

      const filter = ref('all')
      return {taskStore , filter}
    }
  }
</script>


