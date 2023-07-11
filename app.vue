<script setup lang="ts">
import {
  BuildingOffice2Icon,
  PaintBrushIcon,
  SparklesIcon,
  WrenchScrewdriverIcon,
  ComputerDesktopIcon,
  UsersIcon,
  Bars3BottomRightIcon,
  XMarkIcon,
  MagnifyingGlassIcon,
  DocumentDuplicateIcon,
  ShieldCheckIcon,
  UserGroupIcon,
  ShareIcon,
  PhotoIcon,
} from '@heroicons/vue/24/outline'

import { CheckIcon } from '@heroicons/vue/20/solid'

useHead({
  title: 'Advicehome | Professional & modern websites for financial advisers',
  meta: [
    { name: 'description', content: 'Build a modern and beautiful website for your financial advice firm with ease' },
    { name: 'viewport', content: 'width=device-width,initial-scale=1.0' },
  ],
  htmlAttrs: {
    lang: 'en',
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

  setTimeout(() => {
    formState.value = 'done'
  }, 1500)
}

const listener = () => {
  if (scrolledDown.value && window.scrollY === 0) scrolledDown.value = false
  else if (!scrolledDown.value && window.scrollY > 0) scrolledDown.value = true
}

onMounted(() => document.addEventListener('scroll', listener))
onUnmounted(() => document.removeEventListener('scroll', listener))

const selectedPreview = ref<'modern' | 'corporate' | 'family'>('modern')
const mobileMenuOpen = ref(false)

const waitlist = ref<HTMLElement | null>(null)

function focusWaitlistInput() {
  mobileMenuOpen.value = false
  waitlist.value?.focus()
}
</script>

<template>
  <div
    class="fixed inset-0 z-40 backdrop-blur transition-all sm:hidden"
    :class="[mobileMenuOpen ? 'opacity-100' : 'opacity-0 pointer-events-none']"
    @click.self.stop="mobileMenuOpen = false"
  >
    <div
      class="fixed inset-y-0 right-0 bg-white min-w-[320px] shadow-md transition-all duration-200 ring-1 ring-slate-900/5"
      :class="[mobileMenuOpen ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-[100%]']"
    >
      <div class="flex items-center px-5 py-4">
        <LogoIcon class="w-11 pl-2 py-1" />

        <button type="button" class="ml-auto p-2" @click="mobileMenuOpen = false">
          <XMarkIcon class="w-6 h-6" />
          <span class="sr-only">Close</span>
        </button>
      </div>

      <div class="px-5 py-3">
        <nav>
          <ul>
            <li>
              <a href="#features" @click="mobileMenuOpen = false" class="font-semibold text-slate-800 px-2 py-1 block"
                >Features</a
              >
            </li>
          </ul>
        </nav>
      </div>

      <div class="px-5 py-4">
        <button
          type="button"
          @click="focusWaitlistInput"
          class="flex w-full items-center justify-center appearance-none rounded-lg font-semibold text-blue-600 border-2 border-blue-600 px-3 py-2"
        >
          Join the waitlist
        </button>
      </div>
    </div>
  </div>

  <header
    class="fixed inset-x-0 top-0 z-30 transition-all"
    :class="{ 'bg-white/50 backdrop-blur shadow-sm': scrolledDown }"
  >
    <div class="flex items-center mx-auto max-w-[1350px] px-8">
      <a href="#" class="font-bold py-6 inline-flex text-lg" alt="Logo">
        <Logo class="w-[140px] md:w-[160px]" />
      </a>

      <div class="ml-auto sm:hidden">
        <button type="button" @click="mobileMenuOpen = true">
          <Bars3BottomRightIcon class="w-6 h-6" />
        </button>
      </div>

      <div class="ml-auto items-center hidden sm:flex">
        <nav>
          <ul class="flex items-center pr-2 mr-6 border-r border-slate-400">
            <li><a href="#features" class="px-4 py-2 text-sm font-semibold">Features</a></li>
          </ul>
        </nav>

        <button
          type="button"
          @click="focusWaitlistInput"
          class="rounded-lg leading-5 text-sm font-semibold bg-transparent appearance-none border-2 border-blue-600 px-3 py-2 text-blue-600"
        >
          Join the waitlist
        </button>
      </div>
    </div>
  </header>

  <section class="overflow-hidden bg-slate-50 border-b border-slate-200 relative">
    <div class="absolute inset-x-0 top-0 z-10 overflow-hidden pl-[50%] lg:hidden pointer-events-none">
      <img src="/beams-simple.png" alt="" class="-ml-[39rem] -mt-[80px] w-[113.125rem] max-w-none" />
    </div>

    <div
      class="absolute inset-y-0 hidden w-full min-w-[1360px] bg-[url('/beams.png')] bg-[length:1200px_700px] bg-[position:calc(50%_+_370px)_-20px] bg-no-repeat lg:block pointer-events-none"
    ></div>

    <div class="max-w-[1350px] mx-auto px-8 pb-24">
      <div class="flex w-full items-center md:pt-[150px] pt-[120px]">
        <div class="max-w-[650px] md:min-w-[650px] mx-auto">
          <h1 class="font-extrabold text-3xl md:text-5xl text-slate-950 lg:leading-[50px] tracking-tight">
            Create a beautiful, modern adviser website with complete ease.
          </h1>

          <p class="md:leading-[30px] text-slate-600 mt-4 max-w-[570px] text-lg">
            Stun your clients, convert more leads and supercharge your online presence. A brand new platform designed
            for financial advisers and created by experts.
          </p>

          <form @submit.prevent="attemptJoinWaitlist" class="mt-8 max-w-[600px]">
            <label for="email" class="inline-block font-semibold mb-2 text-sm text-slate-800">
              Join the waitlist for early access:
            </label>

            <div class="md:flex md:items-center md:space-x-4">
              <input
                id="email"
                ref="waitlist"
                type="email"
                class="sm:text-sm sm:text-[1rem] text-slate-800 leading-5 px-4 py-3 border-none rounded-lg shadow ring-1 ring-slate-950/5 flex-1 outline-none focus:ring-2 focus:ring-blue-500 w-full md:w-auto"
                placeholder="email@company.co.uk"
                autofocus
                required
              />

              <button
                type="submit"
                class="text-sm rounded-lg leading-5 px-5 py-[13px] text-white font-semibold inline-flex items-center justify-center appearance-none outline-none w-[150px] max-h-[46px] mt-4 md:mt-0"
                :class="{
                  'bg-gradient-to-tr to-sky-500 from-blue-600 focus:ring-2 ring-blue-500 shadow': formState === 'idle',
                  'bg-slate-500 cursor-default': formState === 'processing',
                  'bg-green-600 cursor-default': formState === 'done',
                }"
                :disabled="formState === 'processing' || formState === 'done'"
              >
                <span v-if="formState === 'idle'">Join the waitlist</span>
                <span v-else-if="formState === 'processing'">
                  <Spinner class="w-6 h-6 text-white animate-spin-slow"
                /></span>
                <span v-else-if="formState === 'done'" class="inline-flex items-center space-x-2">
                  <CheckIcon class="w-6 h-6 text-white -ml-2" />
                  <span>Done</span>
                </span>
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
              Use a template as a starter, then easily personalise your website to match your unique brand and voice.
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

  <section id="features" class="bg-white px-8 py-28">
    <div class="lg:max-w-[1350px] max-w-[650px] mx-auto">
      <h2
        class="text-slate-950 font-extrabold text-center text-3xl md:text-4xl max-w-[720px] mx-auto md:leading-[40px] tracking-tight"
      >
        Choose from pages, sections and content crafted specifically for financial advisers.
      </h2>

      <p class="text-center text-lg text-slate-700 mt-4 max-w-[700px] mx-auto">
        A range of precision-built sections for your services, fees, qualifications, testimonials, downloadable guides,
        meet the team, and more.
      </p>

      <div class="mt-10 flex items-center flex-wrap mx-auto max-w-[1000px]">
        <div class="w-full flex justify-center lg:hidden mb-8">
          <div class="rounded-full border border-slate-300 flex items-center p-1 gap-x-1">
            <button
              type="button"
              class="inline-flex items-center appearance-none text-sm font-medium px-[10px] py-1.5 rounded-full"
              :class="{ 'bg-blue-600 text-white shadow': selectedPreview === 'modern' }"
              @click="selectedPreview = 'modern'"
            >
              <ComputerDesktopIcon class="w-5 h-5 mr-2" />
              <span>Modern</span>
            </button>

            <button
              type="button"
              class="inline-flex items-center appearance-none text-sm font-medium px-[10px] py-1.5 rounded-full"
              :class="{ 'bg-blue-600 text-white shadow': selectedPreview === 'corporate' }"
              @click="selectedPreview = 'corporate'"
            >
              <BuildingOffice2Icon class="w-5 h-5 mr-2" />
              <span>Corporate</span>
            </button>

            <button
              type="button"
              class="inline-flex items-center appearance-none text-sm font-medium px-[10px] py-1.5 rounded-full"
              :class="{ 'bg-blue-600 text-white shadow': selectedPreview === 'family' }"
              @click="selectedPreview = 'family'"
            >
              <UsersIcon class="w-5 h-5 mr-2" />
              <span>Family</span>
            </button>
          </div>
        </div>

        <div class="hidden lg:flex flex-col max-w-[340px] -mt-5">
          <div class="text-slate-700 text-sm ml-4">Example websites:</div>

          <div class="p-4 cursor-pointer group" @click="selectedPreview = 'modern'">
            <div
              class="text-lg flex items-center mb-1 transition-all"
              :class="[
                selectedPreview === 'modern'
                  ? 'text-slate-900 font-semibold'
                  : 'text-slate-500 group-hover:text-slate-700 font-medium',
              ]"
            >
              <ComputerDesktopIcon class="w-5 h-5 mr-1.5" />
              <span>Modern</span>
            </div>

            <p
              class="transition-all"
              :class="[selectedPreview === 'modern' ? 'text-slate-700' : 'text-slate-500 group-hover:text-slate-600']"
            >
              Impress your clients with a sleek and modern impression.
            </p>
          </div>

          <div class="p-4 cursor-pointer group" @click="selectedPreview = 'corporate'">
            <div
              class="text-lg flex items-center mb-1 transition-all"
              :class="[
                selectedPreview === 'corporate'
                  ? 'text-slate-900 font-semibold'
                  : 'text-slate-500 group-hover:text-slate-700 font-medium',
              ]"
            >
              <BuildingOffice2Icon class="w-5 h-5 mr-1.5" />
              <span>Corporate</span>
            </div>

            <p
              class="transition-all"
              :class="[
                selectedPreview === 'corporate' ? 'text-slate-700' : 'text-slate-500 group-hover:text-slate-600',
              ]"
            >
              Demonstrate your professionalism and industry expertise to your clients.
            </p>
          </div>

          <div class="p-4 cursor-pointer group" @click="selectedPreview = 'family'">
            <div
              class="text-lg flex items-center mb-1 transition-all"
              :class="[
                selectedPreview === 'family'
                  ? 'text-slate-900 font-semibold'
                  : 'text-slate-500 group-hover:text-slate-700 font-medium',
              ]"
            >
              <UsersIcon class="w-5 h-5 mr-1.5" />
              <span>Family</span>
            </div>

            <p
              class="transition-all"
              :class="[selectedPreview === 'family' ? 'text-slate-700' : 'text-slate-500 group-hover:text-slate-600']"
            >
              For firms wanting a more family-focused and goal-oriented feel.
            </p>
          </div>
        </div>

        <div class="w-full lg:w-auto lg:flex-1">
          <div class="rounded-3xl ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
            <img :src="`/showcase/${selectedPreview}.png`" alt="Showcase image" width="660" height="645" />
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-16">
      <h3 class="text-slate-950 max-w-[780px] text-2xl md:text-3xl font-bold text-center mx-auto tracking-tight">
        We've sweat the details on website best practices, so that you don't have to. Performance, accessibility,
        security and more, taken care of out of the box.
      </h3>

      <div
        class="mt-16 lg:flex flex-wrap text-slate-500 font-medium leading-6 max-w-[700px] mx-auto lg:max-w-none space-y-6 lg:space-y-0"
      >
        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <MagnifyingGlassIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Search Engine Optimisation (SEO)</span>
          <span>. Best practices to help you rank better in Google.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <PhotoIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Image optimisation</span>
          <span>. Any images you use will be auto-adjusted for peak performance.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-3">
          <ShareIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Social media sharing previews</span>
          <span>. Your site will look great, no matter where it gets shared.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <UserGroupIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Accessibility</span>
          <span>. Your site will follow accessibility best practices and be welcoming for all.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <ShieldCheckIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Security</span>
          <span>. Get automatic HTTPS included and spam protection on your contact forms.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <DocumentDuplicateIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Multiple versions</span>
          <span>. Keep your current site up and running while working on a new one.</span>
        </div>
      </div>
    </div>
  </section>

  <section class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-20 xl:flex xl:items-center space-y-16 xl:space-y-0">
      <div class="max-w-[600px] mx-auto xl:mx-0">
        <h2
          class="text-slate-900 font-extrabold text-3xl md:text-4xl leading-[40px] tracking-tight text-center xl:text-left"
        >
          Enjoy
          <span class="bg-gradient-to-b from-sky-500 to-blue-700 bg-clip-text text-transparent"
            >powerful analytics</span
          >
          from inside the Advicehome platform.
        </h2>

        <p class="text-lg text-slate-700 mt-4 text-center xl:text-left">
          Get insights into your traffic, your best performing pages and the most common client journeys throughout your
          website.
        </p>
      </div>

      <div class="flex justify-center xl:pl-8 xl:flex-1">
        <div class="relative inline-flex">
          <div
            class="absolute inset-0 bg-gradient-to-tr from-sky-400 to-blue-600 rounded-lg transform -rotate-3 origin-bottom-left"
          ></div>

          <div class="relative z-10 overflow-hidden rounded-xl shadow-md ring-1 ring-slate-900/5">
            <img src="/analytics.svg" class="flex rounded-xl" alt="Analytics" width="587" height="486" />
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="pt-8 pb-20">
    <div class="px-8 max-w-[1300px] mx-auto">
      <div class="px-12 py-8 bg-white shadow-md rounded-3xl ring-1 ring-slate-950/10">
        <div class="xl:flex xl:items-center">
          <div class="xl:pr-10">
            <div class="font-medium text-lg">Grow your business with a stunning, modern Advicehome website.</div>
            <div class="font-medium text-lg text-slate-500">Join the waitlist for early access.</div>
          </div>

          <div class="mt-6 xl:mt-0 xl:ml-auto flex-1">
            <form @submit.prevent="attemptJoinWaitlist" class="md:flex md:items-center md:space-x-4">
              <input
                id="email"
                ref="waitlist"
                type="email"
                class="sm:text-sm sm:text-[1rem] text-slate-800 leading-5 px-4 py-3 border-none rounded-lg shadow ring-1 ring-slate-950/10 flex-1 outline-none focus:ring-2 focus:ring-blue-500 w-full md:w-auto"
                placeholder="email@company.co.uk"
                autofocus
                required
              />

              <button
                type="submit"
                class="text-sm rounded-lg leading-5 px-5 py-[13px] text-white font-semibold inline-flex items-center justify-center appearance-none outline-none w-[150px] max-h-[46px] mt-4 md:mt-0"
                :class="{
                  'bg-gradient-to-tr to-sky-500 from-blue-600 focus:ring-2 ring-blue-500 shadow': formState === 'idle',
                  'bg-slate-500 cursor-default': formState === 'processing',
                  'bg-green-600 cursor-default': formState === 'done',
                }"
                :disabled="formState === 'processing' || formState === 'done'"
              >
                <span v-if="formState === 'idle'">Join the waitlist</span>
                <span v-else-if="formState === 'processing'">
                  <Spinner class="w-6 h-6 text-white animate-spin-slow"
                /></span>
                <span v-else-if="formState === 'done'" class="inline-flex items-center space-x-2">
                  <CheckIcon class="w-6 h-6 text-white -ml-2" />
                  <span>Done</span>
                </span>
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>

  <footer class="bg-slate-50 border-t border-slate-200 text-[13px] text-slate-500">
    <div class="max-w-[1350px] mx-auto px-8 py-6">&copy; 2023 Advicehome</div>
  </footer>
</template>
