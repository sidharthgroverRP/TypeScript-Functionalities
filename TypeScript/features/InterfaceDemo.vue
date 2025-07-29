<template>
  <div>
    <div><strong>User:</strong> {{ user.name }} (id: {{ user.id }})</div>
    <div><strong>Admin:</strong> {{ admin.name }} (role: {{ admin.role }})</div>
    <div><strong>Email (optional):</strong> {{ user.email || 'N/A' }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

interface User {
  readonly id: number;
  name: string;
  email?: string;
  [key: string]: unknown;
}
type Admin = User & { role: 'admin' };
const user: User = { id: 1, name: 'Alice' };
const admin: Admin = { id: 2, name: 'Bob', role: 'admin' };

export default defineComponent({
  name: 'InterfaceDemo',
  setup() {
    return { user, admin };
  },
});
</script> 