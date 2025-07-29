<template>
  <div>
    <div><strong>Dog:</strong> {{ dog.name }}, Breed: {{ dog.getBreed() }}</div>
    <div><strong>Speak:</strong> {{ message }}</div>
    <div><strong>Static Kingdom:</strong> {{ kingdom }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

class Animal {
  public name: string;
  protected age: number;
  static kingdom = 'Animalia';
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  speak(): string {
    return `${this.name} makes a noise.`;
  }
}
class Dog extends Animal {
  private breed: string;
  constructor(name: string, age: number, breed: string) {
    super(name, age);
    this.breed = breed;
  }
  speak(): string {
    return `${this.name} barks!`;
  }
  getBreed(): string {
    return this.breed;
  }
}

export default defineComponent({
  name: 'ClassDemo',
  setup() {
    const dog = new Dog('Rex', 5, 'Labrador');
    const message = ref(dog.speak());
    const kingdom = Animal.kingdom;
    return { dog, message, kingdom };
  },
});
</script> 