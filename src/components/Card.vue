<template>
  <div
    class="flex flex-col border m-auto w-[50%] bg-[#292730] gap-2 rounded-lg h-[474px]"
  >
    <div
      class="bg-[#1d1d20] border p-4 m-auto w-[90%] rounded-lg mt-8 flex justify-between items-center"
    >
      <h1 class="text-2xl text-[#ffff]">{{ CardHeading }}</h1>
      <img
        alt="Vue logo"
        src="../assets/task_logo.png"
        class="w-[50px] h-[50px]"
      />
    </div>

    <div class="flex gap-2 w-[90%] m-auto justify-center">
      <button
        class="flex items-center bg-[#1f42a2] text-white font-bold py-2 px-4 rounded-lg"
        @click="openTaskModal"
      >
        Add Task
      </button>
    </div>

    <!-- Task List -->
    <div class="task-list w-[90%] h-[330px] overflow-auto m-auto mb-8">
      <div
        v-for="task in tasks"
        :key="task.id"
        class="flex gap-2 justify-between bg-[#1d1d20] border p-4 m-2 rounded-lg"
      >
        <h1 class="text-[#b1b1b4]">{{ task.taskName }}</h1>
        <div class="flex gap-2 items-center">
          <!-- <span class="cursor-pointer">
            <i class="bi bi-eye"></i>
            </span> -->
          <span class="cursor-pointer text-[#b1b1b4]">
            <i class="bi bi-pencil-square"></i>
          </span>
          <span class="cursor-pointer text-[#d9000d]">
            <i class="bi bi-trash"></i>
          </span>
        </div>
      </div>
    </div>
  </div>
  <AddTask :showTaskModal="showTaskModal" @closeModal="showTaskModal = false" />
</template>

<script>
import AddTask from "./modal/AddTask.vue";

export default {
  name: "CardView",
  components: {
    AddTask,
  },
  props: {
    CardHeading: String,
  },
  data() {
    return {
      tasks: [
        { id: 1, taskName: "Task 1 - Complete Vue.js Tutorial" },
        { id: 2, taskName: "Task 2 - Build To-Do App" },
        { id: 3, taskName: "Task 3 - Write Blog Post" },
        { id: 4, taskName: "Task 4 - Attend Team Meeting" },
        { id: 5, taskName: "Task 5 - Review Pull Requests" },
        { id: 6, taskName: "Task 6 - Push Code to GitHub" },
        { id: 7, taskName: "Task 7 - Update Resume" },
        { id: 8, taskName: "Task 8 - Design Portfolio" },
        { id: 9, taskName: "Task 9 - Plan Next Week's Tasks" },
        { id: 10, taskName: "Task 10 - Check Emails" },
      ],
      showTaskModal: false,
    };
  },

  methods: {
    openTaskModal() {
      this.showTaskModal = !this.showTaskModal;
    },
  },
};
</script>

<style scoped>
.task-list::-webkit-scrollbar {
  display: none;
}

.task-list {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
