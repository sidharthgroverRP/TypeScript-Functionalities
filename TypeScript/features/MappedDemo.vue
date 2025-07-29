<template>
  <div>
    <div><strong>Readonly User:</strong> {{ readonlyUser.name }}</div>
    <div><strong>Pick (name only):</strong> {{ userNameOnly.name }}</div>
    <div><strong>Omit (no email):</strong> {{ userWithoutEmail.name }}</div>
    <div><strong>Mapped Type Flags:</strong> {{ JSON.stringify(flags) }}</div>
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

type ReadonlyUser = Readonly<User>;
type UserNameOnly = Pick<User, 'name'>;
type UserWithoutEmail = Omit<User, 'email'>;
type Flags = { [K in 'dark' | 'compact']: boolean };

const readonlyUser: ReadonlyUser = { id: 3, name: 'Readonly' };
const userNameOnly: UserNameOnly = { name: 'NameOnly' };
const userWithoutEmail: UserWithoutEmail = { id: 4, name: 'NoEmail' };
const flags: Flags = { dark: true, compact: false };

export default defineComponent({
  name: 'MappedDemo',
  setup() {
    return { readonlyUser, userNameOnly, userWithoutEmail, flags };
  },
});
</script> 