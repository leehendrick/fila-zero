<script setup>
import {
  Popover,
  PopoverButton,
  PopoverGroup,
  PopoverPanel,
} from "@headlessui/vue";
import {
  Bars3Icon,
  ChatBubbleBottomCenterTextIcon,
  ChatBubbleLeftRightIcon,
  InboxIcon,
  QuestionMarkCircleIcon,
  XMarkIcon,
  ClockIcon,
  FunnelIcon,
  CheckBadgeIcon,
  FaceSmileIcon,
  CalendarDaysIcon,
  BuildingStorefrontIcon,
  EyeIcon,
  FaceFrownIcon,
} from "@heroicons/vue/24/outline";
import { ChevronDownIcon } from "@heroicons/vue/20/solid";
import { ref, onMounted, onBeforeUnmount } from "vue";

const features = [
  {
    name: "Redução do tempo de espera",
    description:
      " FilaZero permite que os clientes agendem atendimentos prévios, reduzindo significativamente o tempo de espera.",
    icon: ClockIcon,
  },
  {
    name: "Aumento da eficiência das operadoras",
    description:
      "Com menos clientes esperando nas filas das lojas, as operadoras podem melhorar sua eficiência no atendimento.",
    icon: FunnelIcon,
  },
  {
    name: "Facilidade de acesso aos serviços",
    description:
      "Ao agendar atendimentos com antecedência, os clientes podem ter um acesso mais conveniente aos serviços de telecomunicações.",
    icon: CheckBadgeIcon,
  },
  {
    name: "Melhoria da satisfação do cliente",
    description:
      "Com um processo de atendimento mais rápido e conveniente, os clientes  experimentarão uma melhoria significativa na satisfação do cliente.",
    icon: FaceSmileIcon,
  },
];
const solutions = [
  {
    name: "Agendar",
    description: "Agende qualquer serviço disponível.",
    href: "#",
    icon: CalendarDaysIcon,
  },
  {
    name: "Ver Lojas",
    description: "Procure lojas perto de si, disponíveis para agendamentos.",
    href: "#",
    icon: BuildingStorefrontIcon,
  },
  {
    name: "Consultar",
    description: "Consulte informações sobre serviços.",
    href: "#",
    icon: EyeIcon,
  },
  {
    name: "Reclamações",
    description: "Faça suas reclamações.",
    href: "#",
    icon: FaceFrownIcon,
  },
];
const navigation = [
  { name: "Página Inicial", href: "#" },
  { name: "Sobre Nós", href: "#" },
  { name: "Contatos", href: "#" },
];
</script>
<template>
  <header class="bg-white dark:bg-gray-900 rounded-br-full">
    <div class="bg-white">
      <header>
        <Popover class="relative bg-white">
          <div
            class="mx-auto flex max-w-7xl items-center justify-between px-6 py-6 md:justify-start md:space-x-10 lg:px-8"
          >
            <div class="flex justify-start lg:w-0 lg:flex-1">
              <a href="#">
                <h1 class="text-4xl font-bold text-blue-500">
                  Fila<span class="text-gray-800">Zero</span>
                </h1>
              </a>
            </div>
            <div class="-my-2 -mr-2 md:hidden">
              <PopoverButton
                class="relative inline-flex items-center justify-center rounded-md bg-white p-2 text-gray-400 hover:bg-gray-100 hover:text-gray-500"
              >
                <span class="absolute -inset-0.5" />
                <span class="sr-only">Open menu</span>
                <Bars3Icon class="h-6 w-6" aria-hidden="true" />
              </PopoverButton>
            </div>
            <PopoverGroup as="nav" class="hidden space-x-10 md:flex">
              <Popover class="relative" v-slot="{ open }">
                <PopoverButton
                  :class="[
                    open ? 'text-gray-900' : 'text-gray-500',
                    'group inline-flex items-center rounded-md bg-white text-lg font-extrabold hover:text-gray-900 ',
                  ]"
                >
                  <span>Serviços</span>
                  <ChevronDownIcon
                    :class="[
                      open ? 'text-gray-600' : 'text-gray-400',
                      'ml-2 h-5 w-5 group-hover:text-gray-500',
                    ]"
                    aria-hidden="true"
                  />
                </PopoverButton>

                <transition
                  enter-active-class="transition ease-out duration-200"
                  enter-from-class="opacity-0 translate-y-1"
                  enter-to-class="opacity-100 translate-y-0"
                  leave-active-class="transition ease-in duration-150"
                  leave-from-class="opacity-100 translate-y-0"
                  leave-to-class="opacity-0 translate-y-1"
                >
                  <PopoverPanel
                    class="absolute z-10 -ml-4 mt-3 w-screen max-w-md transform lg:left-1/2 lg:ml-0 lg:max-w-2xl lg:-translate-x-1/2"
                  >
                    <div
                      class="overflow-hidden rounded-lg shadow-lg ring-1 ring-black ring-opacity-5"
                    >
                      <div
                        class="relative grid gap-6 bg-white px-5 py-6 sm:gap-8 sm:p-8 lg:grid-cols-2"
                      >
                        <a
                          v-for="item in solutions"
                          :key="item.name"
                          :href="item.href"
                          class="-m-3 flex items-start rounded-lg p-3 hover:bg-gray-50"
                        >
                          <div
                            class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-md bg-gray-900 text-white sm:h-12 sm:w-12"
                          >
                            <component
                              :is="item.icon"
                              class="h-6 w-6"
                              aria-hidden="true"
                            />
                          </div>
                          <div class="ml-4">
                            <p class="text-base font-medium text-gray-900">
                              {{ item.name }}
                            </p>
                            <p class="mt-1 text-sm text-gray-500">
                              {{ item.description }}
                            </p>
                          </div>
                        </a>
                      </div>
                    </div>
                  </PopoverPanel>
                </transition>
              </Popover>

              <a
                v-for="item in navigation"
                :key="item.name"
                :href="item.href"
                class="text-lg font-extrabold text-gray-500 hover:text-gray-900"
                >{{ item.name }}</a
              >
            </PopoverGroup>
            <div
              class="hidden items-center justify-end md:flex md:flex-1 lg:w-0"
            >
              <a
                href="#"
                class="whitespace-nowrap text-base font-medium text-gray-500 hover:text-gray-900"
                >Sign in</a
              >
              <a
                href="#"
                class="ml-8 inline-flex items-center justify-center whitespace-nowrap rounded-md border border-transparent bg-blue-500 px-4 py-2 text-base font-medium text-white shadow-sm hover:bg-gray-800"
                >Sign up</a
              >
            </div>
          </div>

          <transition
            enter-active-class="duration-200 ease-out"
            enter-from-class="opacity-0 scale-95"
            enter-to-class="opacity-100 scale-100"
            leave-active-class="duration-100 ease-in"
            leave-from-class="opacity-100 scale-100"
            leave-to-class="opacity-0 scale-95"
          >
            <PopoverPanel
              focus
              class="absolute inset-x-0 top-0 z-30 origin-top-right transform p-2 transition md:hidden"
            >
              <div
                class="divide-y-2 divide-gray-50 rounded-lg bg-white shadow-lg ring-1 ring-black ring-opacity-5"
              >
                <div class="px-5 pb-6 pt-5">
                  <div class="flex items-center justify-between">
                    <div>
                      <h1 class="text-4xl font-bold text-blue-500">
                        Fila<span class="text-gray-800">Zero</span>
                      </h1>
                    </div>
                    <div class="-mr-2">
                      <PopoverButton
                        class="relative inline-flex items-center justify-center rounded-md bg-white p-2 text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500"
                      >
                        <span class="absolute -inset-0.5" />
                        <span class="sr-only">Close menu</span>
                        <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                      </PopoverButton>
                    </div>
                  </div>
                  <div class="mt-6">
                    <nav class="grid grid-cols-1 gap-7">
                      <a
                        v-for="item in solutions"
                        :key="item.name"
                        :href="item.href"
                        class="-m-3 flex items-center rounded-lg p-3 hover:bg-gray-50"
                      >
                        <div
                          class="flex h-10 w-10 flex-shrink-0 items-center justify-center rounded-md bg-indigo-600 text-white"
                        >
                          <component
                            :is="item.icon"
                            class="h-6 w-6"
                            aria-hidden="true"
                          />
                        </div>
                        <div class="ml-4 text-base font-medium text-gray-900">
                          {{ item.name }}
                        </div>
                      </a>
                    </nav>
                  </div>
                </div>
                <div class="px-5 py-6">
                  <div class="grid grid-cols-2 gap-4">
                    <a
                      v-for="item in navigation"
                      :key="item.name"
                      :href="item.href"
                      class="text-base font-medium text-gray-900 hover:text-gray-700"
                      >{{ item.name }}</a
                    >
                  </div>
                  <div class="mt-6">
                    <a
                      href="#"
                      class="flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-600 px-4 py-2 text-base font-medium text-white shadow-sm hover:bg-indigo-700"
                      >Sign up</a
                    >
                    <p
                      class="mt-6 text-center text-base font-medium text-gray-500"
                    >
                      Existing customer?
                      <a href="#" class="text-gray-900">Sign in</a>
                    </p>
                  </div>
                </div>
              </div>
            </PopoverPanel>
          </transition>
        </Popover>
      </header>
    </div>

    <div
      class="grid max-w-screen-xl px-4 py-8 mx-auto lg:gap-8 xl:gap-0 lg:py-16 lg:grid-cols-12"
    >
      <div class="mr-auto place-self-center lg:col-span-7">
        <h1
          class="max-w-2xl mb-4 text-4xl font-extrabold tracking-tight leading-none md:text-5xl xl:text-6xl dark:text-white"
        >
          Agende atendimentos sem filas em lojas de operadoras
        </h1>
        <p
          class="max-w-2xl mb-6 font-light text-gray-500 lg:mb-8 md:text-lg lg:text-xl dark:text-gray-400"
        >
          FilaZero é uma plataforma que visa melhorar a experência dos clientes
          ao permitir que eles agendem horários específicos para serem
          atendidos.
        </p>
        <a
          href="#"
          class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-gray-900 border border-gray-300 rounded-full hover:bg-gray-100 focus:ring-4 focus:ring-gray-100 dark:text-white dark:border-gray-700 dark:hover:bg-gray-700 dark:focus:ring-gray-800"
        >
          Saber mais
        </a>
      </div>
      <div class="hidden lg:mt-0 lg:col-span-5 lg:flex">
        <img src="/static/img/calendar.png" alt="mockup" />
      </div>
    </div>
  </header>
  <section>
    <div class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <div class="p-5 border-b-2 border-gray-900 w-auto">
          <h2
            class="parallax-text text-gray-800 text-4xl font-extrabold text-center mb-8"
          >
            Benefícios da Plataforma
          </h2>
        </div>
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <!-- Cada benefício será adicionado aqui -->
        <!-- Feature section -->
      </div>
      <div class="mx-auto mt-16 max-w-2xl sm:mt-20 lg:mt-24 lg:max-w-4xl">
        <dl
          class="grid max-w-xl grid-cols-1 gap-x-8 gap-y-10 lg:max-w-none lg:grid-cols-2 lg:gap-y-16"
        >
          <div
            v-for="feature in features"
            :key="feature.name"
            class="relative pl-16"
          >
            <dt class="text-lg font-extrabold leading-7 text-gray-900">
              <div
                class="absolute left-0 top-0 flex h-10 w-10 items-center justify-center rounded-lg bg-gray-900"
              >
                <component
                  :is="feature.icon"
                  class="h-6 w-6 text-white"
                  aria-hidden="true"
                />
              </div>
              {{ feature.name }}
            </dt>
            <dd class="mt-2 text-base leading-7 text-gray-600">
              {{ feature.description }}
            </dd>
          </div>
        </dl>
      </div>
    </div>
  </section>
  <section class="py-12 rounded-full bg-gray-900 sm:py-16 lg:py-20">
    <div class="px-4 mx-auto max-w-7xl sm:px-6 lg:px-8">
      <h2 class="text-white text-4xl font-extrabold text-center">
        Operadoras Disponíveis
      </h2>
      <div class="flex justify-center">
        <div
          class="grid justify-center items-center grid-cols-1 mt-5 gap-y-6 sm:grid-cols-2 sm:gap-y-8 lg:grid-cols-3 lg:gap-x-8"
        >
          <img
            class="object-contain w-auto mx-auto h-40"
            src="/static/img/AfricellLogo.png"
            alt="Africell Logo"
          />
          <img
            class="object-contain w-auto mx-auto h-20"
            src="/static/img/unitel-logo.png"
            alt="Unitel Logo"
          />
          <img
            class="object-contain w-auto mx-auto h-40"
            src="/static/img/movicel-logo.png"
            alt="Movicel Logo"
          />
        </div>
      </div>
    </div>
  </section>
  <section class="bg-white">
    <div class="py-8 px-4 mx-auto max-w-screen-xl sm:py-16 lg:px-6">
      <div class="mx-auto max-w-screen-sm text-center">
        <h2
          class="mb-4 text-4xl tracking-tight font-extrabold leading-tight text-gray-900"
        >
          Começe a agendar ainda hoje
        </h2>
        <p class="mb-6 font-light text-gray-500 md:text-lg">
          Try Flowbite Platform for 30 days. No credit card required.
        </p>
        <a
          href="#"
          class="inline-flex border-2 items-center justify-center px-5 py-3 text-base font-medium text-center text-gray-900 border-gray-900 rounded-full hover:text-white hover:bg-gray-900"
        >
          Agendar agora
        </a>
      </div>
    </div>
  </section>
  <!-- Container for demo purpose -->
  <div class="container my-24 mx-auto md:px-6">
    <!-- Section: Design Block -->
    <section class="mb-32 border-t-2 border-gray-900">
      <h2
        class="py-10 flex justify-center mb-4 text-4xl tracking-tight font-extrabold leading-tight text-gray-900"
      >
        Fale connosco
      </h2>
      <div
        class="rounded-lg relative h-[300px] overflow-hidden bg-cover bg-[50%] bg-no-repeat bg-[url('/static/img/contact.jpg')]"
      ></div>
      <div class="container px-6 md:px-12">
        <div
          class="block rounded-lg bg-[hsla(0,0%,100%,0.8)] px-6 py-12 shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-[hsla(0,0%,5%,0.7)] dark:shadow-black/20 md:py-16 md:px-12 -mt-[100px] backdrop-blur-[30px]"
        >
          <div class="flex flex-wrap">
            <div
              class="mb-12 w-full shrink-0 grow-0 basis-auto md:px-3 lg:mb-0 lg:w-5/12 lg:px-6"
            >
              <form>
                <div class="relative mb-6" data-te-input-wrapper-init>
                  <input
                    type="text"
                    class="peer block min-h-[auto] w-full rounded border-2 border-gray-900 bg-transparent py-[0.32rem] px-3 leading-[1.6] outline-none transition-all duration-200 ease-linear focus:placeholder:opacity-100 peer-focus:text-white data-[te-input-state-active]:placeholder:opacity-100 motion-reduce:transition-none [&:not([data-te-input-placeholder-active])]:placeholder:opacity-0"
                    placeholder="Name"
                  />
                  <label
                    class="pointer-events-none absolute top-0 left-3 mb-0 max-w-[90%] origin-[0_0] truncate pt-[0.37rem] leading-[1.6] text-white transition-all duration-200 ease-out peer-focus:-translate-y-[0.9rem] peer-focus:scale-[0.8] peer-focus:text-white peer-data-[te-input-state-active]:-translate-y-[0.9rem] peer-data-[te-input-state-active]:scale-[0.8] motion-reduce:transition-non"
                    for="exampleInput90"
                    >Name
                  </label>
                </div>
                <div class="relative mb-6" data-te-input-wrapper-init>
                  <input
                    type="email"
                    class="peer block min-h-[auto] w-full rounded border-2 border-gray-900 bg-transparent py-[0.32rem] px-3 leading-[1.6] outline-none transition-all duration-200 ease-linear focus:placeholder:opacity-100 peer-focus:text-white data-[te-input-state-active]:placeholder:opacity-100 motion-reduce:transition-none [&:not([data-te-input-placeholder-active])]:placeholder:opacity-0"
                    id="exampleInput91"
                    placeholder="Email address"
                  />
                  <label
                    class="pointer-events-none absolute top-0 left-3 mb-0 max-w-[90%] origin-[0_0] truncate pt-[0.37rem] leading-[1.6] text-gray-900 transition-all duration-200 ease-out peer-focus:-translate-y-[0.9rem] peer-focus:scale-[0.8] peer-focus:text-primary peer-data-[te-input-state-active]:-translate-y-[0.9rem] peer-data-[te-input-state-active]:scale-[0.8] motion-reduce:transition-none dark:text-neutral-200 dark:peer-focus:text-primary"
                    >Email address
                  </label>
                </div>
                <div class="relative mb-6" data-te-input-wrapper-init>
                  <textarea
                    class="peer block min-h-[auto] w-full rounded border-2 border-gray-900 bg-transparent py-[0.32rem] px-3 leading-[1.6] outline-none transition-all duration-200 ease-linear focus:placeholder:opacity-100 peer-focus:text-white data-[te-input-state-active]:placeholder:opacity-100 motion-reduce:transition-none [&:not([data-te-input-placeholder-active])]:placeholder:opacity-0"
                    rows="3"
                    placeholder="Your message"
                  ></textarea>
                  <label
                    for="exampleFormControlTextarea1"
                    class="pointer-events-none absolute top-0 left-3 mb-0 max-w-[90%] origin-[0_0] truncate pt-[0.37rem] leading-[1.6] text-neutral-500 transition-all duration-200 ease-out peer-focus:-translate-y-[0.9rem] peer-focus:scale-[0.8] peer-focus:text-primary peer-data-[te-input-state-active]:-translate-y-[0.9rem] peer-data-[te-input-state-active]:scale-[0.8] motion-reduce:transition-none dark:text-neutral-200 dark:peer-focus:text-primary"
                    >Message</label
                  >
                </div>
                <button
                  type="button"
                  data-te-ripple-init
                  data-te-ripple-color="light"
                  class="mb-6 inline-block w-full rounded bg-gray-900 px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white hover:shadow-[0_4px_9px_-4px_#3b71ca] transition duration-150 ease-in-out lg:mb-0"
                >
                  Send
                </button>
              </form>
            </div>
            <div class="w-full shrink-0 grow-0 basis-auto lg:w-7/12">
              <div class="flex flex-wrap">
                <div
                  class="mb-12 w-full shrink-0 grow-0 basis-auto md:w-6/12 md:px-3 lg:w-full lg:px-6 xl:w-6/12"
                >
                  <div class="flex items-start">
                    <div class="shrink-0">
                      <div
                        class="inline-block rounded-md bg-primary-100 p-4 text-primary"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke-width="2"
                          stroke="currentColor"
                          class="h-6 w-6 text-gray-900"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M14.25 9.75v-4.5m0 4.5h4.5m-4.5 0l6-6m-3 18c-8.284 0-15-6.716-15-15V4.5A2.25 2.25 0 014.5 2.25h1.372c.516 0 .966.351 1.091.852l1.106 4.423c.11.44-.054.902-.417 1.173l-1.293.97a1.062 1.062 0 00-.38 1.21 12.035 12.035 0 007.143 7.143c.441.162.928-.004 1.21-.38l.97-1.293a1.125 1.125 0 011.173-.417l4.423 1.106c.5.125.852.575.852 1.091V19.5a2.25 2.25 0 01-2.25 2.25h-2.25z"
                          />
                        </svg>
                      </div>
                    </div>
                    <div class="ml-6 grow">
                      <p class="mb-2 font-bold dark:text-white">
                        Technical support
                      </p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        support@example.com
                      </p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        +1 234-567-89
                      </p>
                    </div>
                  </div>
                </div>
                <div
                  class="mb-12 w-full shrink-0 grow-0 basis-auto md:w-6/12 md:px-3 lg:w-full lg:px-6 xl:w-6/12"
                >
                  <div class="flex items-start">
                    <div class="shrink-0">
                      <div
                        class="inline-block rounded-md bg-primary-100 p-4 text-primary"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke-width="2"
                          stroke="currentColor"
                          class="h-6 w-6 text-gray-900"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M2.25 18.75a60.07 60.07 0 0115.797 2.101c.727.198 1.453-.342 1.453-1.096V18.75M3.75 4.5v.75A.75.75 0 013 6h-.75m0 0v-.375c0-.621.504-1.125 1.125-1.125H20.25M2.25 6v9m18-10.5v.75c0 .414.336.75.75.75h.75m-1.5-1.5h.375c.621 0 1.125.504 1.125 1.125v9.75c0 .621-.504 1.125-1.125 1.125h-.375m1.5-1.5H21a.75.75 0 00-.75.75v.75m0 0H3.75m0 0h-.375a1.125 1.125 0 01-1.125-1.125V15m1.5 1.5v-.75A.75.75 0 003 15h-.75M15 10.5a3 3 0 11-6 0 3 3 0 016 0zm3 0h.008v.008H18V10.5zm-12 0h.008v.008H6V10.5z"
                          />
                        </svg>
                      </div>
                    </div>
                    <div class="ml-6 grow">
                      <p class="mb-2 font-bold dark:text-white">
                        Sales questions
                      </p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        sales@example.com
                      </p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        +1 234-567-89
                      </p>
                    </div>
                  </div>
                </div>
                <div
                  class="mb-12 w-full shrink-0 grow-0 basis-auto md:mb-0 md:w-6/12 md:px-3 lg:mb-12 lg:w-full lg:px-6 xl:w-6/12"
                >
                  <div class="align-start flex">
                    <div class="shrink-0">
                      <div
                        class="inline-block rounded-md bg-primary-100 p-4 text-primary"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke-width="2"
                          stroke="currentColor"
                          class="h-6 w-6"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M12 7.5h1.5m-1.5 3h1.5m-7.5 3h7.5m-7.5 3h7.5m3-9h3.375c.621 0 1.125.504 1.125 1.125V18a2.25 2.25 0 01-2.25 2.25M16.5 7.5V18a2.25 2.25 0 002.25 2.25M16.5 7.5V4.875c0-.621-.504-1.125-1.125-1.125H4.125C3.504 3.75 3 4.254 3 4.875V18a2.25 2.25 0 002.25 2.25h13.5M6 7.5h3v3H6v-3z"
                          />
                        </svg>
                      </div>
                    </div>
                    <div class="ml-6 grow">
                      <p class="mb-2 font-bold dark:text-white">Press</p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        press@example.com
                      </p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        +1 234-567-89
                      </p>
                    </div>
                  </div>
                </div>
                <div
                  class="w-full shrink-0 grow-0 basis-auto md:w-6/12 md:px-3 lg:w-full lg:px-6 xl:mb-12 xl:w-6/12"
                >
                  <div class="align-start flex">
                    <div class="shrink-0">
                      <div
                        class="inline-block rounded-md bg-primary-100 p-4 text-primary"
                      >
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke-width="2"
                          stroke="currentColor"
                          class="h-6 w-6"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M12 12.75c1.148 0 2.278.08 3.383.237 1.037.146 1.866.966 1.866 2.013 0 3.728-2.35 6.75-5.25 6.75S6.75 18.728 6.75 15c0-1.046.83-1.867 1.866-2.013A24.204 24.204 0 0112 12.75zm0 0c2.883 0 5.647.508 8.207 1.44a23.91 23.91 0 01-1.152 6.06M12 12.75c-2.883 0-5.647.508-8.208 1.44.125 2.104.52 4.136 1.153 6.06M12 12.75a2.25 2.25 0 002.248-2.354M12 12.75a2.25 2.25 0 01-2.248-2.354M12 8.25c.995 0 1.971-.08 2.922-.236.403-.066.74-.358.795-.762a3.778 3.778 0 00-.399-2.25M12 8.25c-.995 0-1.97-.08-2.922-.236-.402-.066-.74-.358-.795-.762a3.734 3.734 0 01.4-2.253M12 8.25a2.25 2.25 0 00-2.248 2.146M12 8.25a2.25 2.25 0 012.248 2.146M8.683 5a6.032 6.032 0 01-1.155-1.002c.07-.63.27-1.222.574-1.747m.581 2.749A3.75 3.75 0 0115.318 5m0 0c.427-.283.815-.62 1.155-.999a4.471 4.471 0 00-.575-1.752M4.921 6a24.048 24.048 0 00-.392 3.314c1.668.546 3.416.914 5.223 1.082M19.08 6c.205 1.08.337 2.187.392 3.314a23.882 23.882 0 01-5.223 1.082"
                          />
                        </svg>
                      </div>
                    </div>
                    <div class="ml-6 grow">
                      <p class="mb-2 font-bold dark:text-white">Bug report</p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        bugs@example.com
                      </p>
                      <p class="text-neutral-500 dark:text-neutral-200">
                        +1 234-567-89
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- Section: Design Block -->
  </div>
  <!-- Container for demo purpose -->
  <footer class="bg-white shadow dark:bg-gray-900">
    <div class="w-full max-w-screen-xl mx-auto p-4 md:py-8">
      <div class="sm:flex sm:items-center sm:justify-between">
        <h1 class="text-4xl font-bold text-blue-500">
          Fila<span class="text-gray-700">Zero</span>
        </h1>
        <ul
          class="flex flex-wrap items-center mb-6 text-sm font-medium text-gray-500 sm:mb-0 dark:text-gray-400"
        >
          <li>
            <a href="#" class="hover:underline me-4 md:me-6">About</a>
          </li>
          <li>
            <a href="#" class="hover:underline me-4 md:me-6">Privacy Policy</a>
          </li>
          <li>
            <a href="#" class="hover:underline me-4 md:me-6">Licensing</a>
          </li>
          <li>
            <a href="#" class="hover:underline">Contact</a>
          </li>
        </ul>
      </div>
      <hr
        class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8"
      />
      <span
        class="block text-sm text-gray-500 sm:text-center dark:text-gray-400"
        >© 2024
        <a href="https://flowbite.com/" class="hover:underline">FilaZero</a>.
        All Rights Reserved.</span
      >
    </div>
  </footer>
</template>
