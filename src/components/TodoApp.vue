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
                <!-- table head -->
                <div class="flex border-[1px] border-gray-400 mt-5 bg-gray-100">
                    <div class="w-[70%] p-2 border-r-[1px] border-gray-400">Task</div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400">Status</div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400">Do</div>
                    <div class="w-[10%] text-center p-2">Undo</div>
                </div>
                <!-- table body -->
                <div class="flex border-[1px] border-gray-400 bg-white" v-for="(task, index) in tasks" :key="index">
                    <div class="w-[70%] p-2 border-r-[1px] border-gray-400" :class="{'finished': task.status === 'finished'}">
                        {{task.name}}
                    </div>
                    <div class="w-[10%] font-semibold p-2 border-r-[1px] text-center border-gray-400 text-sm" @click="changeStatus(index)">
                        <span class="pointer" 
                            :class="{'text-red-800':task.status === 'to-do',
                            'text-red-400':task.status === 'in-progress',
                            'text-green-400':task.status === 'finished'}">
                            {{firstCharUpper(task.status)}}
                        </span>
                    </div>
                    <div class="w-[10%] p-2 border-r-[1px] text-center border-gray-400 cursor-pointer" @click="editTask(index)"><span class="fa fa-pen"></span></div>
                    <div class="w-[10%] text-center p-2 cursor-pointer" @click="deleteTask(index)"><span class="fa fa-trash" ></span></div>
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
            task:'',
            editedTask: null,
            availableStatuses:['to-do', 'in-progress', 'finished'],
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
                }
            ]
        }
    },

    methods:{
        submitTask(){
            if(this.task.length === 0) return ;
            if(this.editedTask === null){
                    this.tasks.push({
                    name: this.task,
                    status: "to-do"
                });
            }else{
                this.tasks[this.editedTask].name = this.task;
                this.editedTask = null;
            }

            this.task = '';
        },
        editTask(index){
            this.task = this.tasks[index].name;
            this.editedTask = index;
        },
        deleteTask(index){
            this.tasks.splice(index, 1);
        },
        changeStatus(index){
            let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
            if(++newIndex > 2) newIndex = 0;
            this.tasks[index].status = this.availableStatuses[newIndex];
        },
        firstCharUpper(str){
            console.log(str)
            return str.charAt(0).toUpperCase() + str.slice(1)
        }
    }
  }
  </script>
  <style>
    .pointer{
        cursor: pointer;
    }
  </style>
  