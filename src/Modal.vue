<template>

   <div class="overlay" :style="{
            display:`${ (state=='close') ? 'none' : 'flex'}`
          }">
    <div class="content">
      <header>
        <h1><slot>{{pages[state]}}</slot></h1>
        <button class="icon" @click="$emit('modal', 'close')"><svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24"><path fill="var(--color-tone-3)" d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"></path></svg></button>
      </header>
      <div class="content-container">
        <div v-if="state == 'settings'">
            <Settings />
        </div>
        <div v-else>
            <Info />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import Info from "./Info.vue"
import Settings from "./Settings.vue"

defineProps<{
  state: String
}>()

defineEmits<{
  (e: 'modal', type: string,info:string): void
}>()

var pages = {'info':'როგორ ვითამაშოთ','settings':'პარამეტრები'}
</script>

<style scoped>
    .overlay {
      display: none;
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      justify-content: center;
      background-color: var(--color-background);
      animation: SlideIn 100ms linear;
      z-index: 2000;
    }

    :host([open]) .overlay {
      display: flex;
    }

    .content {
      position: relative;
      color: var(--color-tone-1);
      padding: 0 32px;
      max-width: var(--game-max-width);
      width: 100%;
      overflow-y: auto;
      height: 100%;
      display: flex;
      flex-direction: column;
    }

    .content-container {
      height: 100%;
    }

    .overlay.closing {
      animation: SlideOut 150ms linear;
    }

    header {
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    h1 {
      font-weight: 700;
      font-size: 16px;
      letter-spacing: 0.5px;
      text-transform: uppercase;
      text-align: center;
      margin-bottom: 10px;
    }

    button {
      position: absolute;
      right: 0;
      user-select: none;
      cursor: pointer;
    }

    @media only screen and (min-device-width : 320px) and (max-device-width : 480px) {
      .content {
        max-width: 100%;
        padding: 0;
      }
      button {
        padding: 0 16px;
      }
    }

    @keyframes SlideIn {
      0% {
        transform: translateY(30px);
        opacity: 0;
      }
      100% {
        transform: translateY(0px);
        opacity: 1;
      }
    }
    @keyframes SlideOut {
      0% {
        transform: translateY(0px);
        opacity: 1;
      }
      90% {
        opacity: 0;
      }
      100% {
        opacity: 0;
        transform: translateY(60px);
      }
    }
</style>