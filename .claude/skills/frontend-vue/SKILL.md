---
name: frontend-vue
description: Strict conventions and rules for writing Vue 3, Vuetify, TypeScript, and ESLint frontend code
---

# Frontend Development Conventions (Vue 3 + Vuetify + Strict TypeScript)

Apply these rules whenever writing, modifying, or refactoring frontend code.

---

## 1. Single File Component (SFC) Layout

Every `.vue` file must follow this exact section order:
1. `<template>`
2. `<script>` (types/interfaces block, if any)
3. `<script setup>` (implementation block)
4. `<style scoped>` (or `<style>`)

### Script Tag Separation
- **`<script lang="ts">`**: Contains ONLY types and interfaces (including Props and Emits interfaces).
- **`<script setup lang="ts">`**: Contains all imports, reactive variables, computed properties, helper functions, lifecycle hooks, and template logic.
- **No Exported Interfaces in `.vue`**: Never use `export interface` inside a `.vue` file.
  - If an interface is needed in more than 1 file $\rightarrow$ place it in the `models/` directory.
  - If a function is needed in more than 1 file $\rightarrow$ place it in the `utils/` directory.

### SFC Example
```vue
<template>
  <v-btn
    :loading="isLoading"
    :disabled="disabled"
    @click="handleClick"
  >
    {{ label }}
  </v-btn>
</template>

<script lang="ts">
interface Props {
  label: string;
  disabled?: boolean;
}

interface Emits {
  (event: 'submit'): void;
}
</script>

<script setup lang="ts">
import { ref, watch } from 'vue';

const props = withDefaults(defineProps<Props>(), {
  disabled: false,
});

const emit = defineEmits<Emits>();

const isLoading = ref<boolean>(false);

function handleClick(): void {
  emit('submit');
}
</script>

<style scoped>
/* Component styles */
</style>
```

---

## 2. Code Quality & Type Safety

- **No `any` Allowed**: Always use strict typing. If a type is genuinely unknown, use `unknown` with narrowing type guards.
- **Strict Equality**: Always use `===` and `!==`. Never use `==` or `!=`.
- **Explicit Condition Checks (NO Falsy Coercion)**:
  - NEVER use `(!value)` or implicit truthy/falsy checks.
  - Always write explicit comparisons:
    - Null/Undefined: `val !== null && val !== undefined` (or `val === null || val === undefined`)
    - Empty string: `str === ''` or `str !== ''`
    - Empty array: `arr.length === 0` or `arr.length > 0`
    - Number check: `typeof num === 'number' && !isNaN(num)`
    - Boolean check: `flag === false` or `flag === true`
- **Explicit `ref` Typing**: Always explicitly type refs (e.g., `ref<boolean>(false)`, `ref<string>('')`, `ref<UserItem | null>(null)`).
- **No Code Comments**: Do not write comments in the code unless strictly necessary to explain genuinely complex, non-obvious algorithms or edge cases.
- **Modular Components**: Avoid huge monolithic files. Extract reusable, self-contained components with clear, indicative names.

---

## 3. Reactivity & Lifecycle Rules

- **Prefer `watch` over `onMounted` for Prop-Dependent Logic**:
  - When component logic depends on a prop, do NOT rely on `onMounted` alone, because prop changes after mount will not trigger `onMounted`.
  - Always use `watch(() => props.targetProp, (newVal) => { ... }, { immediate: true })`.

---

## 4. API & Network Layer

- **Requests Directory**: All API calls must reside in the `requests/` directory.
- **Loadable Composables**: Consume API endpoints via loadable functions/composables that expose reactive state:
  ```typescript
  // Pattern in requests/ or composables/
  export function useFetchUserData() {
    const data = ref<UserData | null>(null);
    const isLoading = ref<boolean>(false);
    const error = ref<string | null>(null);

    async function execute(userId: string): Promise<void> {
      isLoading.value = true;
      error.value = null;
      try {
        data.value = await fetchUserApi(userId);
      } catch (err: unknown) {
        error.value = err instanceof Error ? err.message : 'Unknown error';
      } finally {
        isLoading.value = false;
      }
    }

    return { data, isLoading, error, execute };
  }
  ```

---

## 5. Verification & ESLint

- **Mandatory ESLint Run**: After finishing writing or updating frontend code, always run ESLint across the touched files:
  ```bash
  npm run lint
  # or npx eslint <filepath> --fix
  ```
- Fix all reported ESLint and TypeScript errors before considering the task complete.
