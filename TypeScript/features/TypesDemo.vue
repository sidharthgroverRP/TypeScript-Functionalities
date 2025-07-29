<template>
  <div>
    <div><strong>Union Type Result:</strong> {{ result.type === 'success' ? result.data : result.message }}</div>
    <div><strong>Intersection Type:</strong> {{ withTimestamp.name }} @ {{ withTimestamp.timestamp.toLocaleTimeString() }}</div>
    <div><strong>Literal Type:</strong> {{ color }}</div>
    <div><strong>Template Literal Type:</strong> {{ templateLiteralExample }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue';

interface User {
  readonly id: number;
  name: string;
  email?: string;
  [key: string]: unknown;
}

type Success = { type: 'success'; data: string };
type Error = { type: 'error'; message: string };
type Result = Success | Error;
type WithTimestamp<T> = T & { timestamp: Date };
type Color = 'red' | 'green' | 'blue';
type EventName = `on${Capitalize<string>}`;

const user: User = { id: 1, name: 'Alice' };
const result: Result = { type: 'success', data: 'Loaded' };
const withTimestamp: WithTimestamp<User> = { ...user, timestamp: new Date() };
const color: Color = 'green';

export default defineComponent({
  name: 'TypesDemo',
  setup() {
    const templateLiteralExample = computed(() => 'onClick');
    return { result, withTimestamp, color, templateLiteralExample };
  },
});
</script> 