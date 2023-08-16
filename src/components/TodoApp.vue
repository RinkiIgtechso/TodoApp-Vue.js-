<template>
    <div class="bg-green-200 items-center">
        <div class="flex justify-between place-items-center p-7 text-4xl font-semibold">
            <div>
                Learning 
            </div>
            <div>
                <img src="../assets/logo.png" alt="logo" />
            </div>
            <div>
                Vue.js
            </div>
        </div>
        <div class="px-4 py-6">
            <div class="flex w-[40%] m-auto">
                <input v-model="task" type="text" placeholder="Enter text" class="w-full border-none rounded-md py-2 pl-3 outline-none" >
                <button @click="submitTask" class="border-none p-3 text-white bg-green-800">Submit</button>
            </div>
            <div class="w-[70%] m-auto">
                <div class="flex border-[1px] border-gray-400 mt-5 bg-gray-50">
                    <div class="w-[70%] p-2 border-r-[1px] border-gray-400">Task</div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400">Status</div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400">Do</div>
                    <div class="w-[10%] text-center p-2">Undo</div>
                </div>
                <div class="flex border-[1px] border-gray-400 bg-white" v-for="(task, index) in tasks" :key="index">
                    <div class="w-[70%] p-2 border-r-[1px] border-gray-400">{{task.name}}</div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400 text-sm">{{task.status}}</div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400 "><span class="fa fa-pen cursor-pointer"></span></div>
                    <div class="w-[10%] text-center p-2"><span class="fa fa-trash cursor-pointer"></span></div>
                </div>
            </div>
        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TodoApp',
    props: {
      msg: String
    },
    
    data(){
        return {
            task:"Enter new task",
            tasks:[
                {
                    name:'Steal bananas from shop',
                    status:'to-do'
                },
                {
                    name:'Eat 1kg chocolate in 1 hour',
                    status:'in-progress'
                },
                {
                    name:'Steal toffee from shop',
                    status:'to-do'
                },
                {
                    name:'Eat 20 ice-cream in 1 hour',
                    status:'in-progress'
                }
            ]
        }
    },

    methods:{
        submitTask(){
            console.log(this.task)
        }
    }
  }
  </script>
  