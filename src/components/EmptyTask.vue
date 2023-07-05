<template>
  <Clipboard size="45" />
  <div class="flex flex-col">
    <span class="font-bold">Você ainda não tem tarefas cadastradas</span>
  </div>
</template>

<script>
import { Clipboard } from "lucide-vue-next";
export default {
  name: "EmptyTask",
  components: {
    Clipboard,
  },
};
</script>

<style></style>
