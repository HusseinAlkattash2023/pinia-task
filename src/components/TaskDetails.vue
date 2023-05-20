<template>
    <div class="task">
        <h3>{{task.title}}</h3>
        <div class="icons">
            <i @click="taskStore.deleteTask(task.id)" class="bi bi-trash-fill"></i>
            <i :class="{active:task.isFav}" @click="taskStore.toggleFav(task.id)" class="bi bi-heart-fill"></i>
        </div>
    </div>
</template>

<script>
import { useTaskStore } from '../store/TaskStore'
    export default {
        props:['task'],
        setup(){
            const taskStore = useTaskStore();
            return{taskStore}
        }

    }
</script>