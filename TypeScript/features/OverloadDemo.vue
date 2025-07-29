<template>
  <div>
    <div><strong>Reverse string:</strong> {{ reversedStr }}</div>
    <div><strong>Reverse array:</strong> {{ reversedArr.join(', ') }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

function reverse(input: string): string;
function reverse<T>(input: T[]): T[];
function reverse(input: any): any {
  if (typeof input === 'string') {
    return input.split('').reverse().join('');
  }
  return input.slice().reverse();
}

export default defineComponent({
  name: 'OverloadDemo',
  setup() {
    const str = 'TypeScript';
    const arr = [1, 2, 3];
    const reversedStr = reverse(str);
    const reversedArr = reverse(arr);
    return { reversedStr, reversedArr };
  },
});
</script> 