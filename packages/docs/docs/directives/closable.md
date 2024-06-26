---
title: vClosable
description: vClosable is a Vue 3 directive to trigger a function when the user clicks outside an element, you can exclude some elements
---

# {{ $frontmatter.title }}

{{ $frontmatter.description }}

## Basic usage

<ComponentDemo>
  <div
    id="container"
    style="padding: 50px; background-color: var(--maz-color-bg-lighter);"
    class="flex flex-center rounded"
  >
    <MazCard v-closable="{
      handler: clikedOutside,
      exclude: ['#container']
    }">
      Click outside from the container
    </MazCard>
  </div>

  <div
    v-if="hasClikedOutside"
    style="padding: 16px; margin-top: 16px; background-color: var(--maz-color-success); color: black;"
    class="flex flex-center rounded"
  >
    You clicked outside
  </div>

  <template #code>

  ```vue
  <template>
    <div
      id="container"
      style="padding: 50px; background-color: var(--maz-color-bg-lighter);"
      class="flex flex-center rounded"
    >
      <MazCard v-closable="{
        handler: clikedOutside,
        exclude: ['#container']
      }">
        Click outside from the container
      </MazCard>
    </div>

    <div
      v-if="hasClikedOutside"
      style="padding: 16px; margin-top: 16px; background-color: var(--maz-color-success); color: black;"
      class="flex flex-center rounded"
    >
      You clicked outside
    </div>
  </template>

  <script lang="ts" setup>
    import { vClickOutside } from 'maz-ui'
    import { ref } from 'vue'

    const hasClikedOutside = ref(false)

    const clikedOutside = () => {
      hasClikedOutside.value = true
      setTimeout(() => hasClikedOutside.value = false, 2000)
    }
  </script>
  ```

  </template>
</ComponentDemo>

## Global install

`main.ts`

```typescript
import { createApp } from 'vue'
import { vClosableInstall } from 'maz-ui'

const app = createApp(App)

app.use(vClosableInstall)

app.mount('#app')
```

## Types

```ts
type vClosableBindingValue = (...args: any[]) => any | {
  handler: (...args: any[]) => any
  exclude?: string[]
}
```

<script lang="ts" setup>
  import { ref } from 'vue'
  import { vClosable } from 'maz-ui'

  const hasClikedOutside = ref(false)

  const clikedOutside = () => {
    hasClikedOutside.value = true
    setTimeout(() => hasClikedOutside.value = false, 2000)
  }
</script>
