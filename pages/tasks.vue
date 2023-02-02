<template>
    <div class="">
        <div class="text-5xl flex justify-center font-semibold">
            <h1>Todos</h1>

        </div>
        <br>
        <div class="flex justify-center">
            <div class="border-2 h-[275px] relative min-h-max w-11/12 border-gray-200 rounded-lg">
                <h1 class="p-3 pl-5 text-[18px] bg-gray-100 border-b-2 rounded-t-lg">Add a task</h1>
                <h1 class="text-[18px] pt-6 pl-5">Items</h1>

                <div class="pl-5 pt-3">
                    
                    <input class="pl-2 w-12/13 text-[18px] border-2 h-[40px] max-w-full" type="text" placeholder="What do you want to do?" v-model="todo" v-on:keyup.enter="add"/>

                </div>
                <p class="p-3 pl-6 text-[14px] text-gray-600">Enter what you want to procastinate 😃</p>
                <div class="pl-6 mb-5">
                      <button class="p-3
                     bg-blue-600
                      rounded
                     text-white
                      " @click="add">Add Task</button>
                      <br>
                </div>
            </div>
        </div>

        <br><br>
          <div class="flex justify-center">
            <div class="border-2 h-[500px] max-h-full max-w-full md: relative w-11/12 border-gray-200 rounded-lg">
                <h1 class="p-3 pl-5 text-[18px] bg-gray-100 border-b-2 rounded-t-lg">Tasks</h1>
                    <div class="text-[18px] ml-8 mt-8">
                        <div class="pl-10 font-bold text-[18px] mb-4 grid grid-cols-3">
                            <p>Items</p>
                            <p>Status</p>
                            <p>Action</p>
                        </div>
                        <div class="text-[18px] p-3 grid grid-cols-3" v-for="(a,index) in list" :key="index">
                            <p>{{ a.name }}</p>
                            <p>{{ a.status }}</p>
                            <div class="flex space-x-2">
                                <button class="p-3
                                bg-blue-600
                                rounded
                                text-white
                                " @click="taskdone(a)">Complete</button>
                                <button class="p-2
                                bg-red-600
                                rounded
                                text-white
                                " @click="removetask(index)">Delete</button>
                      
                            </div>
                        </div>
                        </div>
                    </div>
                </div>
            </div>
        
</template>

<script setup="ts">
import { ref, onMounted } from 'vue'

const status = ref(false)
const list = reactive([])

const todo = ref('')

const add = () => {
    console.log(todo.value, 'todo')

    if(todo.value == '') return alert('input field is empty')
  
    let item = {
        name: todo.value,
        status: 'Not completed',
    }

    list.push(item)

    todo.value = ''

}

const taskdone = (a) => {
    status.value = true
    console.log(a,'index')
    if(status){
        a.status = "Completed"
    }
    else{
        a.status = "Not Completed"
    }
}
const removetask = (index) => {

  
    list.splice(index, 1)
}
</script>