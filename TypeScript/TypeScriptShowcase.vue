<template>
  <div class="showcase-app">
    <header class="header-bar">
      <h1>TypeScript Feature Showcase</h1>
      <p class="subtitle">Explore TypeScript features interactively in Vue 3</p>
    </header>
    <main class="features-grid">
      <section v-for="feature in features" :key="feature.title" class="feature-card">
        <h2>{{ feature.title }}</h2>
        <p class="feature-desc">{{ feature.description }}</p>
        <component :is="feature.component" />
      </section>
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ClassDemo from './features/ClassDemo.vue';
import InterfaceDemo from './features/InterfaceDemo.vue';
import EnumDemo from './features/EnumDemo.vue';
import GenericsDemo from './features/GenericsDemo.vue';
import TypesDemo from './features/TypesDemo.vue';
import MappedDemo from './features/MappedDemo.vue';
import OverloadDemo from './features/OverloadDemo.vue';
import InferenceDemo from './features/InferenceDemo.vue';

const features = [
  {
    title: 'Classes & Inheritance',
    description: 'Demonstrates classes, inheritance, access modifiers, and static properties.',
    component: ClassDemo,
  },
  {
    title: 'Interfaces & Types',
    description: 'Shows interfaces, types, optional/readonly properties, and index signatures.',
    component: InterfaceDemo,
  },
  {
    title: 'Enums',
    description: 'Demonstrates enum usage.',
    component: EnumDemo,
  },
  {
    title: 'Generics, Utility Types, Type Guards, as',
    description: 'Shows generics, Partial, Record, type guards, and type assertions.',
    component: GenericsDemo,
  },
  {
    title: 'Union, Intersection, Literal, Template Literal Types',
    description: 'Demonstrates union, intersection, literal, and template literal types.',
    component: TypesDemo,
  },
  {
    title: 'Mapped Types, Readonly, Pick, Omit',
    description: 'Shows mapped types, Readonly, Pick, and Omit utility types.',
    component: MappedDemo,
  },
  {
    title: 'Function Overloads',
    description: 'Demonstrates function overloads.',
    component: OverloadDemo,
  },
  {
    title: 'Type Inference, Narrowing, Index Signatures',
    description: 'Shows type inference, narrowing, and index signatures.',
    component: InferenceDemo,
  },
];

export default defineComponent({
  name: 'TypeScriptShowcase',
  components: {
    ClassDemo,
    InterfaceDemo,
    EnumDemo,
    GenericsDemo,
    TypesDemo,
    MappedDemo,
    OverloadDemo,
    InferenceDemo,
  },
  setup() {
    return { features };
  },
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

.showcase-app {
  font-family: 'Inter', Arial, sans-serif;
  background: linear-gradient(120deg, #f8fafc 0%, #e0e7ef 100%);
  min-height: 100vh;
}
.header-bar {
  background: #2d3748;
  color: #fff;
  padding: 2rem 0 1rem 0;
  text-align: center;
  box-shadow: 0 2px 8px rgba(44,62,80,0.08);
}
.header-bar h1 {
  margin: 0;
  font-size: 2.5rem;
  font-weight: 600;
  letter-spacing: 1px;
}
.subtitle {
  margin-top: 0.5rem;
  font-size: 1.15rem;
  color: #cbd5e1;
}
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
  gap: 2rem;
  max-width: 1100px;
  margin: 2.5rem auto;
  padding: 0 1.5rem 2rem 1.5rem;
}
.feature-card {
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 4px 24px rgba(44,62,80,0.10);
  border: 1px solid #e2e8f0;
  padding: 2rem 1.5rem 1.5rem 1.5rem;
  transition: box-shadow 0.2s, transform 0.2s;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  min-height: 260px;
  position: relative;
}
.feature-card:hover {
  box-shadow: 0 8px 32px rgba(44,62,80,0.18);
  transform: translateY(-4px) scale(1.02);
  border-color: #a0aec0;
}
.feature-card h2 {
  margin-top: 0;
  font-size: 1.35rem;
  font-weight: 600;
  color: #2d3748;
}
.feature-desc {
  color: #64748b;
  font-size: 1rem;
  margin-bottom: 1.1rem;
}
@media (max-width: 600px) {
  .features-grid {
    grid-template-columns: 1fr;
    padding: 0 0.5rem 2rem 0.5rem;
  }
  .feature-card {
    padding: 1.2rem 0.7rem 1rem 0.7rem;
  }
  .header-bar h1 {
    font-size: 1.5rem;
  }
}
</style> 