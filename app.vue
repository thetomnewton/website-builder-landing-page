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
  FingerPrintIcon,
} from '@heroicons/vue/24/outline'

import { CheckIcon, ExclamationCircleIcon } from '@heroicons/vue/20/solid'

const email = ref('')

useHead({
  title: 'Advicehome | Professional & modern websites for financial advisers',
  meta: [
    { name: 'description', content: 'Build a modern and beautiful website for your financial advice firm with ease' },
    {
      name: 'twitter:description',
      content: 'Build a modern and beautiful website for your financial advice firm with ease',
    },
    {
      name: 'og:description',
      content: 'Build a modern and beautiful website for your financial advice firm with ease',
    },
    { name: 'theme-color', content: '#ffffff' },
    { name: 'viewport', content: 'width=device-width,initial-scale=1.0' },
    { property: 'twitter:site', content: '@advicehome_' },
    { property: 'twitter:creator', content: '@advicehome_' },
    { property: 'og:site_name', content: 'Advicehome' },
    { property: 'og:type', content: 'website' },
    { property: 'twitter:card', content: 'summary_large_image' },
    { property: 'twitter:image', content: 'https://www.advicehome.co.uk/social.png' },
    { property: 'og:image', content: 'https://www.advicehome.co.uk/social.png' },
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

async function attemptJoinWaitlist() {
  formState.value = 'processing'

  try {
    await fetch('https://api.advicehome.co.uk/sanctum/csrf-cookie')
    await fetch('https://api.advicehome.co.uk/api/waitlist/join', {
      method: 'post',
      credentials: 'include',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        email: email.value,
      }),
    })
    formState.value = 'done'
  } catch (e) {
    formState.value = 'error'
  }
}

const listener = () => {
  if (scrolledDown.value && window.scrollY === 0) scrolledDown.value = false
  else if (!scrolledDown.value && window.scrollY > 0) scrolledDown.value = true
}

onMounted(() => document.addEventListener('scroll', listener))
onUnmounted(() => document.removeEventListener('scroll', listener))

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
        <span class="sr-only">Advicehome</span>
      </a>

      <div class="ml-auto sm:hidden">
        <button type="button" @click="mobileMenuOpen = true">
          <Bars3BottomRightIcon class="w-6 h-6" />
          <span class="sr-only">Menu</span>
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
          <h1 class="font-extrabold text-3xl md:text-5xl text-slate-950 lg:leading-[56px] tracking-tight">
            Create a beautiful, modern adviser website with complete ease.
          </h1>

          <p class="md:leading-[30px] text-slate-600 mt-5 max-w-[570px] text-lg">
            Stun your clients, convert more leads and supercharge your online presence. A brand new platform designed
            for financial advisers and created by expert designers.
          </p>

          <form @submit.prevent="attemptJoinWaitlist" class="mt-8 max-w-[600px]">
            <label for="email" class="inline-block font-semibold mb-2 text-sm text-slate-800">
              Join the waitlist for early access and discounts:
            </label>

            <div class="md:flex md:items-center md:space-x-4">
              <input
                id="email"
                ref="waitlist"
                v-model="email"
                @focus="formState = 'idle'"
                @input="formState = 'idle'"
                type="email"
                class="sm:text-sm sm:text-[1rem] text-slate-800 leading-5 px-4 py-3 rounded-lg shadow ring-1 ring-slate-950/5 flex-1 focus:ring-2 focus:ring-blue-500 w-full md:w-auto appearance-none"
                placeholder="email@company.co.uk"
                required
              />

              <button
                type="submit"
                class="text-sm rounded-lg leading-5 px-5 py-[13px] text-white font-semibold inline-flex items-center justify-center appearance-none outline-none w-[150px] max-h-[46px] mt-4 md:mt-0"
                :class="{
                  'bg-gradient-to-tr to-sky-500 from-blue-600 focus:ring-2 ring-blue-500 shadow': formState === 'idle',
                  'bg-slate-500 cursor-default': formState === 'processing',
                  'bg-red-500 cursor-default': formState === 'error',
                  'bg-green-600 cursor-default': formState === 'done',
                }"
                :disabled="formState === 'processing' || formState === 'error' || formState === 'done'"
              >
                <span v-if="formState === 'idle'">Join the waitlist</span>
                <span v-else-if="formState === 'processing'">
                  <Spinner class="w-6 h-6 text-white animate-spin-slow"
                /></span>
                <span v-else-if="formState === 'error'" class="inline-flex items-center space-x-2">
                  <ExclamationCircleIcon class="w-6 h-6 text-white -ml-2" />
                  <span>Error</span>
                </span>
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

      <div class="mt-10 mb-4 text-center font-medium">Choose from dozens of templates including:</div>

      <div class="flex-wrap mx-auto max-w-[1000px]">
        <div class="w-full lg:w-auto lg:flex-1 flex flex-wrap">
          <div class="lg:p-3 lg:w-1/2">
            <div class="rounded-3xl ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
              <img :src="`/showcase/modern.png`" alt="Showcase image" />
            </div>

            <div class="p-4 cursor-pointer group">
              <div class="text-lg flex items-center mb-1 transition-all font-semibold">
                <ComputerDesktopIcon class="w-5 h-5 mr-1.5" />
                <span>Modern</span>
              </div>

              <p class="transition-all">Impress your clients with a sleek and modern brand, with splashes of colour.</p>
            </div>
          </div>
          <div class="lg:p-3 lg:w-1/2">
            <div class="rounded-3xl ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
              <img :src="`/showcase/corporate.png`" alt="Showcase image" />
            </div>

            <div class="p-4 cursor-pointer group">
              <div class="text-lg flex items-center mb-1 transition-all font-semibold">
                <BuildingOffice2Icon class="w-5 h-5 mr-1.5" />
                <span>Corporate</span>
              </div>

              <p class="transition-all">Demonstrate your professionalism and industry expertise to your clients.</p>
            </div>
          </div>
          <div class="lg:p-3 lg:w-1/2">
            <div class="rounded-3xl ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
              <img :src="`/showcase/sleek.png`" alt="Showcase image" />
            </div>

            <div class="p-4 cursor-pointer group">
              <div class="text-lg flex items-center mb-1 transition-all font-semibold">
                <FingerPrintIcon class="w-5 h-5 mr-1.5" />
                <span>Sleek</span>
              </div>

              <p class="transition-all">
                For firms looking for a darker and more exclusive brand, with intricate details.
              </p>
            </div>
          </div>

          <div class="lg:p-3 lg:w-1/2">
            <div class="rounded-3xl ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
              <img :src="`/showcase/family.png`" alt="Showcase image" />
            </div>

            <div class="p-4 cursor-pointer group">
              <div class="text-lg flex items-center mb-1 transition-all font-semibold">
                <UsersIcon class="w-5 h-5 mr-1.5" />
                <span>Family</span>
              </div>

              <p class="transition-all">For firms wanting a more family-focused and goal-oriented feel.</p>
            </div>
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
        <div class="lg:w-1/3 lg:px-4 lg:py-4">
          <MagnifyingGlassIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Search Engine Optimisation (SEO)</span>
          <span>. Best practices to help you rank better in Google.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-4">
          <PhotoIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Image optimisation</span>
          <span>. Any images you use will be auto-adjusted for peak performance.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-4">
          <ShareIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Social media sharing previews</span>
          <span>. Your site will look great, no matter where it gets shared.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-4">
          <UserGroupIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Accessibility</span>
          <span>. Your site will follow accessibility best practices and be welcoming for all.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-4">
          <ShieldCheckIcon class="text-black inline w-5 h-5 mr-1.5" />
          <span class="text-black">Security</span>
          <span>. Get automatic HTTPS included and spam protection on your contact forms.</span>
        </div>

        <div class="lg:w-1/3 lg:px-4 lg:py-4">
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
          Get
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
    <div class="max-w-[1300px] mx-auto px-8 xl:px-0">
      <div
        class="px-8 sm:px-12 py-8 bg-gradient-to-b from-white to-slate-50 via-white shadow-md rounded-3xl ring-1 ring-slate-950/10"
      >
        <div class="xl:flex xl:items-center">
          <div class="xl:pr-10">
            <div class="font-medium text-lg">Grow your business with a stunning Advicehome website.</div>
            <div class="font-medium text-lg text-slate-500">Join the waitlist for early access and discounts:</div>
          </div>

          <div class="mt-6 xl:mt-0 xl:ml-auto flex-1">
            <form @submit.prevent="attemptJoinWaitlist" class="md:flex md:items-center md:space-x-4">
              <input
                id="email-lower"
                ref="waitlist"
                v-model="email"
                @focus="formState = 'idle'"
                @input="formState = 'idle'"
                type="email"
                class="sm:text-sm sm:text-[1rem] text-slate-800 leading-5 px-4 py-3 rounded-lg shadow ring-1 ring-slate-950/10 flex-1 focus:ring-2 focus:ring-blue-500 w-full md:w-auto appearance-none"
                placeholder="email@company.co.uk"
                required
              />

              <button
                type="submit"
                class="text-sm rounded-lg leading-5 px-5 py-[13px] text-white font-semibold inline-flex items-center justify-center appearance-none outline-none w-[150px] max-h-[46px] mt-6 md:mt-0"
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

  <footer
    class="bg-gradient-to-b from-white to-slate-50 via-white border-t border-slate-200 text-[13px] text-slate-500"
  >
    <div class="max-w-[1350px] mx-auto px-8 py-8 sm:flex sm: items-center">
      <div class="">
        <svg viewBox="0 0 19 21" fill="none" xmlns="http://www.w3.org/2000/svg" class="text-slate-500 w-8">
          <path
            d="M16 8C15.5 7 10 2.5 9 2.5C7.99999 2.5 2.5 7 2 8C1.5 9 1 16 2.5 17.5C4 19 14 19 15.5 17.5C17 16 16.5 9 16 8Z"
            stroke="currentColor"
            stroke-width="1.3"
          />
          <rect x="6" y="14.2" width="6" height="1.3" rx="0.9" fill="currentColor" />
        </svg>
      </div>

      <div class="sm:ml-auto sm:flex sm:items-center sm:mt-0 mt-6">
        <div>&copy; 2023 Advicehome</div>
        <a
          href="//twitter.com/AdvicehomeApp"
          target="_blank"
          rel="noreferrer"
          class="sm:ml-6 mt-3 sm:mt-0 hover:underline text-slate-700 font-medium flex items-center"
        >
          <svg viewBox="0 0 20 20" aria-hidden="true" class="h-5 w-5 fill-slate-400 mr-2">
            <path
              d="M6.29 18.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0 0 20 3.92a8.19 8.19 0 0 1-2.357.646 4.118 4.118 0 0 0 1.804-2.27 8.224 8.224 0 0 1-2.605.996 4.107 4.107 0 0 0-6.993 3.743 11.65 11.65 0 0 1-8.457-4.287 4.106 4.106 0 0 0 1.27 5.477A4.073 4.073 0 0 1 .8 7.713v.052a4.105 4.105 0 0 0 3.292 4.022 4.095 4.095 0 0 1-1.853.07 4.108 4.108 0 0 0 3.834 2.85A8.233 8.233 0 0 1 0 16.407a11.615 11.615 0 0 0 6.29 1.84"
            ></path>
          </svg>
          <div>Follow us on Twitter</div>
        </a>
      </div>
    </div>
  </footer>
</template>
