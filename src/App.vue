<script setup lang="ts">

import { ref, type Ref } from 'vue'

interface Data {
  slip?: {
    id?: number,
    advice?: string,
  },
}

const adviceData: Ref<Data | null> = ref(null)

async function fetchData() {
  adviceData.value = null
  const res = await fetch(
    `https://api.adviceslip.com/advice`
  )
  adviceData.value = await res.json()
}

fetchData()

</script>

<template>
  <div class="grid place-items-center h-screen grid-cols-3 p-3">
    <div class="col-span-3">
      <div class="">
        <figure
          class="relative gap-6 flex items-center flex-col-reverse neutralColor2 rounded-lg px-6 pt-8 pb-20 dark:bg-slate-800 dark:highlight-white/5">
          <button @click="fetchData"
            class="transition ease-in-out delay-150 hover:-translate-y-1 hover:scale-110 duration-300 bg-green-400 hover:shadow-green-400 shadow-2xl rounded-full flex flex-col items-center justify-center absolute h-14 w-14 -bottom-6"><svg
              width="24" height="24" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z"
                fill="#202733" />
            </svg></button>
          <figcaption class="flex flex-col items-center">
            <svg width="295" height="16" xmlns="http://www.w3.org/2000/svg">
              <g fill="none" fill-rule="evenodd">
                <path fill="#4F5D74" d="M0 8h122v1H0zM173 8h122v1H173z" />
                <g transform="translate(138)" fill="#CEE3E9">
                  <rect width="6" height="16" rx="3" />
                  <rect x="14" width="6" height="16" rx="3" />
                </g>
              </g>
            </svg>
          </figcaption>
          <blockquote>
            <p class="text-lg text-slate-200 text-center leading-relaxed">
              {{ adviceData?.slip?.advice }}
            </p>
          </blockquote>
          <figcaption class="flex flex-col items-center mt-3 secondaryColor">
            <div class="text-xs tracking-widest">ADVICE #{{ adviceData?.slip?.id }}</div>
          </figcaption>
        </figure>
      </div>
    </div>
    <div class="col-start-2 text-slate-200 absolute bottom-5">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="https://github.com/diarih">Diar Ihza</a>.
    </div>
  </div>
</template>

<style>
@import './assets/base.css';
</style>
