<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import { Select } from 'radix-vue/namespaced';

const fruits: [name: string, emoji: string][] =
  [
    ['Apple', '🍏'],
    ['Banana', '🍌'],
    ['Orange', '🍊'],
    ['Pineapple', '🍍'],
    ['Watermelon', '🍉'],
    ['Strawberry', '🍓'],
    ['Blueberry', '🍋'],
    ['Blackberry', '🍑'],
    ['Raspberry', '🍁']
  ]
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <hr class="my-8">

  <main class="container">
    <Select.Root>
      <Select.Trigger
        class="inline-flex justify-center gap-x-1.5 rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50">

        <Select.Value placeholder="Select a fruit" />
      </Select.Trigger>

      <Select.Portal>
        <Select.Content :side-offset="4" class="bg-white w-56 rounded-md shadow-md" position="popper">
          <Select.Item v-for="fruit in fruits" :value="fruit[0]" :key="fruit[0]">
            <kbd>
              {{ fruit[1] }}
            </kbd>

            <Select.ItemText>
              {{ fruit[0] }}
            </Select.ItemText>
          </Select.Item>
        </Select.Content>
      </Select.Portal>
    </Select.Root>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
