<template lang="pug">
div
  Disclosure.bg-white(as="nav" v-slot="{ open }")
    div(class='sm:px-6 lg:px-8 max-w-7xl.mx-auto.px-5' )
      .flex.items-center.justify-between.h-19
        .flex.items-center
          .flex-shrink-1#logo
            img(src="/karma.png" alt="Workflow")
          div#menunavtengah(class="md:block hidden")
            .ml-10.flex.items-baseline.space-x-4
              template(v-for="(item, itemIdx) in navigation" :key="item")
                template(v-if="(itemIdx === 0)")
                  // Current: "bg-gray text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white"
                  router-link(to='/')
                    .bg-gray-900.text-white.px-3.py-2.rounded-md.text-lg.font-large {{ item.title }}
                a(v-else="" href="howto" class="text-gray-300 px-3 py-2 rounded-md text-lg font-large hover:bg-gray-700 hover:text-white") {{ item.title }}
        div#connectright(class="hidden md:block")
          div(class="md:ml-6 ml-4 flex items-center")
            a(href="#" @click="panggil()" class="text-gray-300 px-3 py-2 rounded-md text-lg font-medium hover:bg-gray-700 hover:text-white border-2") connect
    DisclosurePanel(class="md:hidden")
      div(class="sm:px-3 px-2 pt-2 pb-3 space-y-1")
        template(v-for="(item, itemIdx) in navigation" :key="item")
          template(v-if="(itemIdx === 0)")
            // Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white"
            a.bg-gray-900.text-white.block.px-3.py-2.rounded-md.text-base.font-medium(href="{{item.link}}") {{ item.title }}
          a(v-else="" href="{{item.link}}" class="hover:bg-gray-700 hover:text-white text-gray-300 block px-3 py-2 rounded-md text-base font-medium") {{ item.title }}
  header.bg-white
    div(class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8")
  main
    div(class="sm:px-6 lg:px-8 max-w-7xl mx-auto py-6")
      // Replace with your content
      div(class="sm:px-0 px-4 py-6")
        .border-0.border-dashed.border-gray-200.rounded-lg.h-96
          router-view
      // /End replace
</template>

<script>
import { Disclosure, DisclosureButton, DisclosurePanel, Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { BellIcon, MenuIcon, XIcon } from '@heroicons/vue/outline'
import web3modal from './lib/web3modal'
import Web3 from 'web3'

// On login button click...

// const provider = await web3modal.connect()
async function openweb3modal() {
  const provider = await web3modal.connect()
  console.log(provider)
  // alert ('test ini dari method')
}

// Save provider in state

// import ModalAlt from '@/components/ModalAlt.vue' 
const navigation = [{title :'About', link:'/how'},{title:'How To', link:'/mint'}]
const uprofile = ['Mint', 'Settings', 'Sign out']
// import { Core } from '@self.id/core'

// connect to a known URL
// const core = new Core({ ceramic: 'testnet-clay' })
// const profile = await core.get('basicProfile', id)
export default {
  components: {
    Disclosure,
    DisclosureButton,
    DisclosurePanel,
    Menu,
    MenuButton,
    MenuItem,
    MenuItems,
    BellIcon,
    MenuIcon,
    XIcon,
  },
  setup() {
    return {
      navigation,
      uprofile,
      // profile,
    }
    
  },
  methods: {
    panggil() {
      // alert('test')
      openweb3modal()
    }
  }
}
</script>