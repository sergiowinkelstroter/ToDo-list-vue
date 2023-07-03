<template>
  <ul class="flex flex-col mt-6 gap-3 text-gray-100">
    <li
      v-for="(item, index) in tasks"
      :key="item"
      class="w-full flex justify-between p-4 bg-gray-400 rounded-md"
      :class="{ 'opacity-70': item.completed }"
    >
      <div class="flex gap-4 items-center">
        <input
          type="checkbox"
          id="checkbox"
          :checked="item.completed"
          @change="toggleTask(index)"
          class="w-4 h-4"
        />
        <span :class="{ 'line-through': item.completed }">
          {{ item.name }}</span
        >
      </div>
      <button @click="deleteTask(index)"><Trash2 /></button>
    </li>
  </ul>
</template>

<script>
import { Trash2 } from "lucide-vue-next";
export default {
  name: "ListTasks",
  props: {
    tasks: Array,
    toggleTask: Function,
    deleteTask: Function,
  },
  components: {
    Trash2,
  },
};
</script>

<style></style>
