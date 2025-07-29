<template>
  <div>
    <div><strong>Identity Generic:</strong> {{ genericValue }}</div>
    <div><strong>Partial User:</strong> {{ JSON.stringify(partialUser) }}</div>
    <div><strong>User Record:</strong> {{ JSON.stringify(userRecord) }}</div>
    <div><strong>Type Guard (isString):</strong> {{ isStr ? 'Yes' : 'No' }}</div>
    <div><strong>Type Assertion (as):</strong> {{ upperTestVal }}</div>
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
type Admin = User & { role: 'admin' };
const user: User = { id: 1, name: 'Alice' };
const admin: Admin = { id: 2, name: 'Bob', role: 'admin' };

type PartialUser = Partial<User>;
type UserRecord = Record<number, User>;

function identity<T>(value: T): T { return value; }
function isString(val: unknown): val is string { return typeof val === 'string'; }

const genericValue = identity<string>('Hello Generics');
const partialUser: PartialUser = { name: 'Partial' };
const userRecord: UserRecord = { 1: user, 2: admin };

export default defineComponent({
  name: 'GenericsDemo',
  setup() {
    const testVal: unknown = 'hello';
    const isStr = isString(testVal);
    const upperTestVal = computed(() => (testVal as string).toUpperCase());
    return { genericValue, partialUser, userRecord, isStr, upperTestVal };
  },
});
</script> 