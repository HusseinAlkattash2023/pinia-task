<template>
    <div>
        <form @submit.prevent="handelSubmit">
            <input type="text" placeholder="I need to..." v-model="newTask"/>
            <button>Add</button>
        </form>
    </div>
</template>

<script>
import {useTaskStore} from "../store/TaskStore";
import {ref} from "vue";

    export default {
        setup(){
            const taskStore = useTaskStore();

            const newTask = ref('')

            const handelSubmit = ()=>{
                if(newTask.value.length > 0){
                    taskStore.addTask({
                        title:newTask.value,
                        isFav:false,
                        id:Math.floor(Math.random()*10)
                    })
                    newTask.value = ''
                }
            }
            return {handelSubmit , newTask}
        }
    }
</script>