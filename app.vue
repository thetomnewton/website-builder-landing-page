<script setup lang="ts">
import {
  BuildingOffice2Icon,
  PaintBrushIcon,
  SparklesIcon,
  WrenchScrewdriverIcon,
  ComputerDesktopIcon,
  UsersIcon,
  Bars3BottomRightIcon,
} from '@heroicons/vue/24/outline'

useHead({
  title: 'Homefront | Professional & modern websites for financial advisers',
  meta: [
    { name: 'description', content: 'Build a modern and beautiful website for your financial advice firm with ease' },
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
    ></div>
  </div>

  <header
    class="fixed inset-x-0 top-0 z-30 transition-all"
    :class="{ 'bg-white/70 backdrop-blur shadow-sm': scrolledDown }"
  >
    <div class="flex items-center mx-auto max-w-[1350px] px-8">
      <a href="/" class="font-bold py-6 inline-flex text-lg">
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
            <li><a href="#" class="px-4 py-2 text-sm font-semibold">Features</a></li>
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
          <h1 class="font-extrabold text-5xl text-slate-950 leading-[50px] tracking-tight">
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

  <section class="bg-white px-8 py-28">
    <div class="lg:max-w-[1350px] max-w-[650px] mx-auto">
      <h2
        class="text-slate-950 font-extrabold text-center text-4xl max-w-[720px] mx-auto leading-[40px] tracking-tight"
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
          <div class="rounded-lg ring-1 ring-slate-900/5 shadow-lg overflow-hidden">
            <img :src="`/showcase/${selectedPreview}.png`" alt="" />
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-24">
      <h2
        class="text-slate-950 font-extrabold text-center text-4xl max-w-[720px] mx-auto leading-[40px] tracking-tight"
      >
        SEO, social sharing, performance, accessibility, all taken care of.
      </h2>

      <p class="text-center text-lg text-slate-700 mt-4 max-w-[700px] mx-auto">
        We sweat the details on best practices such as Search Engine Optimisation (SEO), accessibility, performance,
        designing for mobile devices, social sharing, image optimisation, security, building for production, and so on,
        so you don't have to.
      </p>
    </div>
  </section>

  <section class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-24">
      <h2
        class="text-slate-950 font-extrabold text-center text-4xl max-w-[720px] mx-auto leading-[40px] tracking-tight"
      >
        Enjoy powerful analytics from within the Homefront platform
      </h2>

      <p class="text-center text-lg text-slate-700 mt-4 max-w-[700px] mx-auto">
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Tenetur explicabo blanditiis labore neque velit
        repellat optio officia.
      </p>
    </div>
  </section>

  <section class="bg-white">
    <div class="max-w-[1350px] mx-auto px-8 py-24">
      <h2
        class="text-slate-950 font-extrabold text-center text-4xl max-w-[720px] mx-auto leading-[40px] tracking-tight"
      >
        Take your firm's digital presence to the next level
      </h2>

      <p>
        We have pre-built sections for your services, fees, qualifications, how to find your offices, and many more.
      </p>
    </div>
  </section>

  <footer class="bg-slate-50 border-t border-slate-200 py-32"></footer>
</template>
