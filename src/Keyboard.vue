<script setup lang="ts">
import { LetterState } from './types'

defineProps<{
  letterStates: Record<string, LetterState>
}>()

defineEmits<{
  (e: 'key', key: string): void
}>()

const rows = [
  'ქწერტყუიოპ'.split(''),
  'ასდფგჰჯკლ'.split(''),
  'ზხცვბნმ'.split(''),
  ['Enter', ...'ჭღთშჟძჩ'.split(''), 'Backspace']
]
</script>

<template>
  <div id="keyboard">
    <div class="row" v-for="(row, i) in rows" :key="i">
      <div class="spacer" v-if="i === 2"></div>
      <button
        v-for="(key, i) in row"
        :key="i"
        :class="[key.length > 1 && 'big', letterStates[key]]"
        @click="$emit('key', key)"
      >
        <span v-if="key !== 'Backspace'">{{ key }}</span>
        <svg
          v-else
          xmlns="http://www.w3.org/2000/svg"
          height="24"
          viewBox="0 0 24 24"
          width="24"
        >
          <path
            fill="currentColor"
            d="M22 3H7c-.69 0-1.23.35-1.59.88L0 12l5.41 8.11c.36.53.9.89 1.59.89h15c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H7.07L2.4 12l4.66-7H22v14zm-11.59-2L14 13.41 17.59 17 19 15.59 15.41 12 19 8.41 17.59 7 14 10.59 10.41 7 9 8.41 12.59 12 9 15.59z"
          ></path>
        </svg>
      </button>
      <div class="spacer" v-if="i === 2"></div>
    </div>
  </div>
</template>

<style scoped>
#keyboard {
  margin: 30px 8px 0;
  user-select: none;
}
.row {
  display: flex;
  width: 100%;
  margin: 0 auto 8px;
  touch-action: manipulation;
}
.spacer {
  flex: 0.5;
}


</style>
