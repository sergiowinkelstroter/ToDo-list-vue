<script>
import NewTask from "./components/NewTask.vue";
import ListTasks from "./components/ListTasks.vue";
import EmptyTask from "./components/EmptyTask.vue";
import { ref, computed } from "vue";

export default {
  components: {
    ListTasks,
    NewTask,
    EmptyTask,
  },

  setup() {
    const newTask = ref("");
    const tasks = ref([]);
    const checked = ref(false);

    function updateNewTask(value) {
      newTask.value = value;
    }

    function addTask() {
      if (newTask.value !== "") {
        tasks.value.push({ name: newTask.value, completed: false });
        newTask.value = "";
      } else {
        window.alert("O campo de entrada está vazio.");
      }
    }

    function deleteTask(index) {
      tasks.value.splice(index, 1);
    }

    function toggleTask(index) {
      tasks.value[index].completed = !tasks.value[index].completed;
    }

    const completedTasksCount = computed(() => {
      return tasks.value.filter((task) => task.completed).length;
    });

    return {
      newTask,
      tasks,
      addTask,
      deleteTask,
      checked,
      toggleTask,
      completedTasksCount,
      updateNewTask,
    };
  },
};
</script>

<template>
  <header class="bg-gray-700 w-full h-[180px] flex justify-center items-center">
    <img src="logo.png" alt="" class="" />
  </header>
  <div class="relative flex flex-col justify-center items-center">
    <NewTask
      :newTask="newTask"
      @update:newTask="updateNewTask"
      :addTask="addTask"
    />
  </div>

  <main class="w-[700px] m-auto flex flex-col mt-16 text-blue font-bold">
    <div class="w-full flex justify-between">
      <div class="flex gap-2 items-center">
        <span class="">Tarefas criadas</span>
        <span
          class="bg-gray-400 w-6 h-6 rounded-full flex items-center justify-center"
          >{{ tasks.length }}</span
        >
      </div>
      <div class="flex gap-2 items-center border-1">
        <span class="text-purple">Concluídas</span>
        <span
          class="bg-gray-400 p-2 rounded-full flex items-center justify-center text-purple"
          >{{ completedTasksCount }} de {{ tasks.length }}</span
        >
      </div>
    </div>
    <div v-if="tasks.length > 0">
      <ListTasks
        :tasks="tasks"
        :deleteTask="deleteTask"
        :toggleTask="toggleTask"
      />
    </div>
    <div
      v-else
      class="text-gray-300 flex flex-col gap-3 justify-center items-center mt-6 border-t-2 border-gray-400 p-4"
    >
      <EmptyTask />
    </div>
  </main>
</template>
