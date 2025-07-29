<template>
  <div>
    <div><strong>Status:</strong> {{ enumDemoStatus }}</div>
    <div><strong>All Statuses:</strong> {{ allStatuses }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

enum Status {
  Todo = 'Todo',
  InProgress = 'In Progress',
  Done = 'Done',
}
const enumDemoStatus: Status = Status.InProgress;
const allStatuses = Object.values(Status).join(', ');

export default defineComponent({
  name: 'EnumDemo',
  setup() {
    return { enumDemoStatus, allStatuses };
  },
});
</script> 