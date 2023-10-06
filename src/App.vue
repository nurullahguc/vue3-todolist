<script setup>
import { ref, reactive } from 'vue';
import Actions from "./components/Actions.vue";
import Modal from "./components/Modal.vue"


const showModal = ref(false)
let ModalTitle = "Create New Task"
let tasks = reactive([])

const taskStatus = [
  { name: "Pending", class: "warning" },
  { name: "Completed", class: "success" },
  { name: "Cancelled", class: "danger" },
  { name: "In Progress", class: "info" },
]

</script>

<template>
  <h2 class="text-center">Niko Style To Do List</h2>

  <button @click="showModal = true; ModalTitle = 'Create New Task';" style="display: block;"
    class="btn btn-primary float-right mb-3"> + Add Task</button>

  <table class="table table-bordered mt-5">
    <thead>
      <tr>
        <th>ID</th>
        <th>Task</th>
        <th>Status</th>
        <th>Action</th>
      </tr>
    </thead>
    <tbody>

      <tr v-if="tasks.count > 0" v-for="task in tasks">
        <td>{{ task.id }}</td>
        <td>{{ task.task }}</td>
        <td>{{ task.status }}</td>
        <td>
          <Actions :id="task.id"></Actions>
        </td>
      </tr>
      <tr v-else>
        <td colspan="4" class="text-center font-weight-bold text-danger">There is not any task.</td>
      </tr>
    </tbody>


  </table>


  <Teleport to="body">
    <modal :taskStatus="taskStatus" :show="showModal" :title="ModalTitle" @close="showModal = false"></modal>
  </Teleport>
</template>