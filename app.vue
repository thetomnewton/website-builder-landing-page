<script setup lang="ts">
import { PaintBrushIcon, SparklesIcon, WrenchScrewdriverIcon } from '@heroicons/vue/24/outline'

useHead({
  htmlAttrs: {
    class: 'h-full',
  },
  bodyAttrs: {
    class: 'h-full font-sans antialiased text-slate-900',
  },
})

const formState = ref<'idle' | 'processing' | 'done' | 'error'>('idle')
const scrolledDown = ref(false)

function attemptJoinWaitlist() {
  formState.value = 'processing'
}

const listener = () => {
  if (scrolledDown.value && window.scrollY === 0) scrolledDown.value = false
  else if (!scrolledDown.value && window.scrollY > 0) scrolledDown.value = true
}

onMounted(() => document.addEventListener('scroll', listener))
onUnmounted(() => document.removeEventListener('scroll', listener))
</script>

<template>
  <header
    class="fixed inset-x-0 top-0 z-50 transition-all"
    :class="{ 'bg-white/70 backdrop-blur shadow': scrolledDown }"
  >
    <div class="flex items-center mx-auto max-w-[1350px] px-8">
      <a href="/" class="font-bold py-6 inline-flex text-lg">
        <Logo class="w-[160px]" />
      </a>

      <div class="ml-auto flex items-center">
        <nav>
          <ul class="flex items-center pr-2 mr-6 border-r border-slate-400">
            <li><a href="#" class="px-4 py-2 text-sm font-semibold">Features</a></li>
            <li><a href="#" class="px-4 py-2 text-sm font-semibold">About</a></li>
            <li><a href="#" class="px-4 py-2 text-sm font-semibold">Pricing</a></li>
          </ul>
        </nav>

        <button
          type="button"
          class="rounded-lg leading-5 text-sm font-semibold bg-transparent appearance-none border-2 border-slate-900 px-3 py-2 text-slate-900"
        >
          Join the waitlist
        </button>
      </div>
    </div>
  </header>

  <section class="overflow-hidden bg-slate-50 border-b border-slate-200 relative">
    <div class="absolute inset-x-0 top-0 z-10 overflow-hidden pl-[50%] lg:hidden">
      <img src="/beams-simple.png" alt="" class="-ml-[39rem] -mt-[80px] w-[113.125rem] max-w-none" />
    </div>

    <div
      class="absolute inset-y-0 hidden w-full min-w-[1360px] bg-[url('/beams.png')] bg-[length:1200px_700px] bg-[position:calc(50%_+_370px)_-20px] bg-no-repeat lg:block pointer-events-none"
    ></div>

    <div class="max-w-[1350px] mx-auto px-8 pb-24">
      <div class="flex w-full items-center pt-[150px]">
        <div class="max-w-[650px] md:min-w-[650px] mx-auto">
          <h1 class="font-extrabold text-5xl text-slate-950 leading-[50px]">
            Create a beautiful, modern adviser website with complete ease.
          </h1>

          <p class="leading-[30px] text-slate-600 mt-4 max-w-[620px] text-lg">
            Stun your clients, convert more leads and supercharge your online presence. A brand new platform designed
            for financial advisers and created by experts to give your website the perfect starting point.
          </p>

          <form @submit.prevent="attemptJoinWaitlist" class="mt-8 max-w-[600px]">
            <label for="email" class="inline-block font-semibold mb-2 text-sm text-slate-800">
              Join the waitlist for early access:
            </label>

            <div class="flex items-center space-x-4">
              <input
                id="email"
                type="email"
                class="text-sm sm:text-[1rem] text-slate-800 leading-5 px-4 py-3 rounded-lg shadow border border-slate-200 flex-1 outline-none focus:ring-2 ring-blue-500 focus:border-blue-500"
                placeholder="email@company.co.uk"
                autofocus
                required
              />

              <button
                type="submit"
                class="text-sm rounded-lg leading-5 px-4 py-3 bg-slate-900 text-white border border-slate-900 font-semibold shadow inline-flex items-center justify-center appearance-none outline-none focus:ring-2 ring-slate-400"
              >
                <span>Join the waitlist</span>
              </button>
            </div>
          </form>
        </div>

        <div class="hidden lg:flex">
          <div class="relative flex-shrink-0 p-3">
            <div class="relative z-10 rounded-lg ring-1 ring-slate-900/5 shadow-xl overflow-hidden">
              <img src="/best-ifa-1.png" alt="" class="h-[369px] w-[320px]" />
            </div>
          </div>

          <div class="relative flex-shrink-0 mt-14 p-3">
            <div class="relative z-10 rounded-lg ring-1 ring-slate-900/5 shadow-xl overflow-hidden pb-8 bg-white">
              <img src="/sterling-wisdom-1.png" alt="" class="h-[337px] w-[320px]" />
            </div>
          </div>

          <div class="relative flex-shrink-0 p-3">
            <div class="relative z-10 rounded-lg ring-1 ring-slate-900/5 shadow-xl overflow-hidden pb-8 bg-white">
              <img src="/watson-smith-1.png" alt="" class="h-[337px] w-[320px]" />
            </div>
          </div>
        </div>
      </div>

      <div
        class="lg:flex lg:items-start gap-8 mt-20 max-w-[650px] lg:max-w-none mx-auto lg:mx-0 space-y-8 lg:space-y-0"
      >
        <div class="lg:w-1/3 flex items-start">
          <div
            class="mr-6 w-[38px] h-[38px] shadow bg-blue-50 border border-blue-600 rounded-lg flex items-center justify-center"
          >
            <WrenchScrewdriverIcon class="w-6 h-6 text-blue-600" />
          </div>

          <div class="flex-1">
            <div class="font-semibold">Beautiful hand-crafted templates</div>
            <p class="text-slate-500 mt-3 leading-6">
              Use our catalogue of modern and professional templates, designed with your clients in mind.
            </p>
          </div>
        </div>

        <div class="lg:w-1/3 flex items-start">
          <div
            class="mr-6 w-[38px] h-[38px] shadow bg-blue-50 border border-blue-600 rounded-lg flex items-center justify-center"
          >
            <PaintBrushIcon class="w-6 h-6 text-blue-600" />
          </div>

          <div class="flex-1">
            <div class="font-semibold">Easy to customise to match your brand</div>

            <p class="text-slate-500 mt-3 leading-6">
              Use a template as a starter, then easily personalise your website to match your unique brand.
            </p>
          </div>
        </div>

        <div class="lg:w-1/3 flex items-start">
          <div
            class="mr-6 w-[38px] h-[38px] shadow bg-blue-50 border border-blue-600 rounded-lg flex items-center justify-center"
          >
            <SparklesIcon class="w-6 h-6 text-blue-600" />
          </div>

          <div class="flex-1">
            <div class="font-semibold">Use our content examples, or use AI</div>

            <p class="text-slate-500 mt-3 leading-6">
              Start with our professional content examples, or use AI to generate content to match your writing style.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-24"></div>
  </section>
</template>
