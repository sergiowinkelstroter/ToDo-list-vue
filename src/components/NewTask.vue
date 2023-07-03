<template>
  <div class="absolute flex justify-center items-center gap-4">
    <input
      :value="newTask"
      @input="$emit('update:newTask', $event.target.value)"
      type="text"
      name=""
      id=""
      placeholder="Adicione uma nova tarefa"
      class="w-[500px] h-12 bg-gray-600 text-gray-300 text-base rounded-md pl-3 focus:outline-none"
    />
    <button
      @click="addTask()"
      class="bg-blue-dark text-gray-100 rounded-md w-[90px] h-12 flex items-center justify-center gap-1"
    >
      Criar
      <PlusCircle size="18" />
    </button>
  </div>
</template>

<script>
import { PlusCircle } from "lucide-vue-next";

export default {
  name: "NewTask",
  components: {
    PlusCircle,
  },
  props: {
    addTask: Function,
    newTask: String,
  },
};
</script>
