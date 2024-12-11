<template>
    <div v-if="showTaskModal" class="fixed inset-0 flex items-center justify-center z-50 bg-gray-900 bg-opacity-50">
      <div class="bg-white rounded-lg shadow-lg p-6 max-w-lg w-full">
        <h1 class="text-2xl font-bold mb-4">Add Task</h1>
        <button 
        @click="$emit('closeModal')" 
        class="absolute top-[17%] right-[26%] text-gray-600 hover:text-gray-900">
        <i class="bi bi-x text-2xl"></i>
      </button>
        <div class="mb-4">
          <label for="task-name" class="block text-sm font-semibold text-gray-700 text-left">Task Name</label>
          <input 
            type="text" 
            v-model="taskName" 
            id="task-name" 
            class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-500" 
            placeholder="Enter task name" 
            required 
          />
        </div>
        <div class="mb-4">
          <label for="subtask-heading" class="block text-sm font-semibold text-gray-700 text-left">Subtask Name</label>
          <div id="subtask-list" class="flex justify-between items-center gap-2">
            <div v-for="(subtask, index) in subtasks" :key="index" class="w-full">
              <input 
                type="text" 
                v-model="subtasks[index]" 
                placeholder="Enter subtask" 
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-500"
                required 
              />
            </div>
            <!-- <div class="flex gap-2">
              <button 
                type="button" 
                @click="addSubtask" 
                class="px-2 py-1 bg-green-500 text-white rounded-lg hover:bg-green-400">
                +
              </button>
              <button 
                type="button" 
                @click="removeSubtask" 
                class="px-2 py-1 bg-red-500 text-white rounded-lg hover:bg-red-400">
                -
              </button>
            </div> -->
          </div>
        </div>
        <div class="mb-4">
          <label for="task-date" class="block text-sm font-semibold text-gray-700 text-left">Date</label>
          <input 
            type="date" 
            v-model="taskDate" 
            id="task-date" 
            class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-500" 
            required 
          />
        </div>
  
        <button 
          type="button" 
          @click="submitTask" 
          class="w-full px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-400">
          Create Task
        </button>
  
      
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'AddTask',
    data() {
      return {
        taskName: '',
        subtasks: [''],
        taskDate: '',
        creatorName: ''
      };
    },
    props: {
      showTaskModal: {
        type: Boolean,
        default: false
      }
    },
    methods: {
      addSubtask() {
        this.subtasks.push('');
      },
      removeSubtask() {
        if (this.subtasks.length > 1) {
          this.subtasks.pop();
        }
      },
      submitTask() {
        const taskData = {
          taskName: this.taskName,
          subtasks: this.subtasks,
          taskDate: this.taskDate,
          creatorName: this.creatorName
        };
        console.log('Task Created:', taskData);
        this.$emit('closeModal');
      }
    }
  };
  </script>
  