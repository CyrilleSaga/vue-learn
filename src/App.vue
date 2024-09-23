<script setup>
import AppHeader from "@/components/AppHeader.vue";
import {Badge} from "@/components/ui/badge";
import {Button} from "@/components/ui/button";
import {Input} from "@/components/ui/input";
import {ref} from "vue";
import {Checkbox} from "@/components/ui/checkbox";

const tasks = ref([
  {
    id: 1,
    title: "Faire les courses",
    completed: false,
    data: 1025431512,
  },
  {
    id: 2,
    title: "Faire la cuisine",
    completed: true,
    data: 1025431512,
  },
  {
    id: 3,
    title: "Aller au cinema",
    completed: false,
    data: 1025431512,
  },
]);

</script>

<template>
  <div class="container mt-10 mx-auto">
    <AppHeader/>

    <!--  Add new task section -->
    <div class="flex flex-col items-center justify-center gap-2 mt-4">
      <h1 class="text-start text-2xl">
        Add new task
      </h1>
      <form>
        <div class="flex w-full max-w-sm items-center gap-1.5">
          <Input id="task" type="text" placeholder="Task title" />
          <Button type="submit">
            Add
          </Button>
        </div>
      </form>
    </div>


    <!--  Filters chip section-->
    <div class="flex justify-center items-center gap-2 mt-16">
      <Badge>
        All
      </Badge>
      <Badge>
        Completed
      </Badge>
      <Badge>
        Not completed
      </Badge>
    </div>

    <!--  Task list section -->
    <div class="flex flex-col items-center justify-center gap-4 mt-4">
      <div class="flex flex-col gap-4 w-full max-w-sm">
        <div v-for="task in tasks" :key="task.id" class="flex gap-2 items-center">
          <Checkbox :id="task.id" :checked="task.completed" @update:checked="task.completed = !task.completed" />
          <label :for="task.id" class="text-start text-xl">
            <span :class="task.completed ? 'line-through' : ''">
              {{ task.title }}
            </span>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

