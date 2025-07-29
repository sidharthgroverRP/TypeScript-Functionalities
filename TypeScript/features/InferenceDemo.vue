<template>
  <div>
    <div><strong>Inferred Types:</strong> {{ inferredType }}</div>
    <div><strong>Narrowing:</strong> {{ printValue('hello') }} | {{ printValue(42) }}</div>
    <div><strong>Index Signature:</strong> {{ JSON.stringify(indexObj) }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

const values = [1, 'two', true];
const inferredType = values.map(v => typeof v).join(', ');
function printValue(val: string | number) {
  if (typeof val === 'string') {
    return `String: ${val}`;
  }
  return `Number: ${val}`;
}
const indexObj: { [key: string]: number } = { a: 1, b: 2 };

export default defineComponent({
  name: 'InferenceDemo',
  setup() {
    return { inferredType, printValue, indexObj };
  },
});
</script> 