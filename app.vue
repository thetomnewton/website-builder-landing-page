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
  title: 'Homefront | Professional & modern websites for financial advisers',
  meta: [
    { name: 'description', content: 'Build a modern and beautiful website for your financial advice firm with ease' },
    { name: 'viewport', content: 'width=device-width,initial-scale=1.0' },
  ],
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
            <li>
              <a href="#pricing" @click="mobileMenuOpen = false" class="font-semibold text-slate-800 px-2 py-1 block"
                >Pricing</a
              >
            </li>
          </ul>
        </nav>
      </div>

      <div class="px-5 py-4">
        <button
          type="button"
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
      <a href="#" class="font-bold py-6 inline-flex text-lg">
        <Logo class="w-[160px]" />
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
            <li><a href="#pricing" class="px-4 py-2 text-sm font-semibold">Pricing</a></li>
          </ul>
        </nav>

        <button
          type="button"
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

          <p class="leading-[30px] text-slate-600 mt-4 max-w-[570px] text-lg">
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
                type="email"
                class="text-sm sm:text-[1rem] text-slate-800 leading-5 px-4 py-3 rounded-lg shadow border border-slate-200 flex-1 outline-none focus:ring-2 ring-blue-500 focus:border-blue-500 w-full md:w-auto"
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

      <div class="mt-12 flex items-center flex-wrap mx-auto max-w-[1000px]">
        <div class="w-full flex justify-center lg:hidden mb-8">
          <div class="rounded-lg bg-slate-200 flex items-center p-0.5 gap-x-1">
            <button
              type="button"
              class="inline-flex items-center appearance-none text-sm font-medium px-2 py-1 rounded-md"
              :class="{ 'bg-white shadow': selectedPreview === 'modern' }"
              @click="selectedPreview = 'modern'"
            >
              <ComputerDesktopIcon class="w-5 h-5 mr-2" />
              <span>Modern</span>
            </button>

            <button
              type="button"
              class="inline-flex items-center appearance-none text-sm font-medium px-2 py-1 rounded-md"
              :class="{ 'bg-white shadow': selectedPreview === 'corporate' }"
              @click="selectedPreview = 'corporate'"
            >
              <BuildingOffice2Icon class="w-5 h-5 mr-2" />
              <span>Corporate</span>
            </button>

            <button
              type="button"
              class="inline-flex items-center appearance-none text-sm font-medium px-2 py-1 rounded-md"
              :class="{ 'bg-white shadow': selectedPreview === 'family' }"
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
              :class="[selectedPreview === 'modern' ? 'text-slate-700' : 'text-slate-400 group-hover:text-slate-500']"
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
                selectedPreview === 'corporate' ? 'text-slate-700' : 'text-slate-400 group-hover:text-slate-500',
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
              :class="[selectedPreview === 'family' ? 'text-slate-700' : 'text-slate-400 group-hover:text-slate-500']"
            >
              For firms wanting a more family-focused and goal-oriented feel.
            </p>
          </div>
        </div>

        <div class="w-full lg:w-auto lg:flex-1">
          <div class="rounded-3xl ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
            <img :src="`/showcase/${selectedPreview}.png`" alt="" />
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
        class="mt-16 lg:flex flex-wrap text-slate-500 font-medium leading-6 max-w-[700px] mx-auto lg:max-w-none space-y-4 lg:space-y-0"
      >
        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <MagnifyingGlassIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Search Engine Optimisation (SEO)</span>
          <span>. Best practices to help you rank better in Google.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-2">
          <PhotoIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Image optimisation</span>
          <span>. Any images you use will be adjusted for peak performance.</span>
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
    <div class="max-w-[1350px] mx-auto px-8 py-16 xl:flex xl:items-center space-y-16 xl:space-y-0">
      <div class="max-w-[600px] mx-auto xl:mx-0">
        <h2
          class="text-slate-900 font-extrabold text-3xl md:text-4xl leading-[40px] tracking-tight text-center xl:text-left"
        >
          Enjoy
          <span class="bg-gradient-to-b from-sky-500 to-blue-700 bg-clip-text text-transparent"
            >powerful analytics</span
          >
          from inside the Homefront platform.
        </h2>

        <p class="text-lg text-slate-700 mt-4 text-center xl:text-left">
          Get insights into your traffic, your best performing pages and the most common client journeys throughout your
          website.
        </p>
      </div>

      <div class="flex justify-center">
        <div class="relative inline-flex">
          <div
            class="absolute inset-0 bg-gradient-to-tr from-sky-400 to-blue-600 rounded-lg transform -rotate-3 origin-bottom-left"
          ></div>

          <div class="relative z-10 overflow-hidden rounded-xl shadow-md ring-1 ring-slate-900/5">
            <img src="/analytics.svg" class="flex rounded-xl" alt="Analytics" />
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="pricing" class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-24">
      <h2
        class="text-slate-950 font-extrabold text-center text-4xl max-w-[720px] mx-auto leading-[40px] tracking-tight"
      >
        Take your firm's digital presence to the next level.
      </h2>

      <p class="text-center text-lg text-slate-700 mt-4 max-w-[700px] mx-auto">
        We have pre-built sections for your services, fees, qualifications, how to find your offices, and many more.
      </p>
    </div>
  </section>

  <footer class="bg-slate-50 border-t border-slate-200 py-10"></footer>
</template>
