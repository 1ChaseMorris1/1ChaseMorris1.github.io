<template>
  <Menu as="div" class="relative inline-block">
    <!-- Trigger -->
    <MenuButton
      class="inline-flex w-full justify-center gap-x-1.5 rounded-md px-3 py-2 text-sm font-semibold hover:opacity-90"
      :class="[
        `bg-${bgcolor}`,
        `text-${textcolor}`,
        `rounded-${round}`
      ]"
    >
      {{ label }}
      <ChevronDownIcon class="-mr-1 size-5" :class="`text-${iconcolor}`" aria-hidden="true" />
    </MenuButton>

    <transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transform opacity-0 scale-95"
      enter-to-class="transform scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-from-class="transform scale-100"
      leave-to-class="transform opacity-0 scale-95"
    >
      <MenuItems
        class="absolute z-10 mt-2 w-56 outline outline-1 -outline-offset-1"
        :class="[
          `bg-${bgmenucolor}`,
          `text-${menutextcolor}`,
          `rounded-${menuround}`,
          menuposition
        ]"
      >
        <div class="py-1">
          <MenuItem v-for="(item, i) in items" :key="i" v-slot="{ active }">
            <a
              :href="item.href || '#'"
              :class="[
                'block px-4 py-2 text-sm',
                active ? `bg-${activebg} text-${activetext}` : ''
              ]"
            >
              {{ item.text }}
            </a>
          </MenuItem>
        </div>
      </MenuItems>
    </transition>
  </Menu>
</template>

<script setup>
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'

defineProps({
  label: { type: String, default: 'Options' },
  items: { type: Array, default: () => [{ text: 'Item', href: '#' }] },

  // Button
  bgcolor: { type: String, default: 'white/10' },
  textcolor: { type: String, default: 'white' },
  round: { type: String, default: 'md' },
  iconcolor: { type: String, default: 'gray-400' },
  
  // Menu
  bgmenucolor: { type: String, default: 'gray-800' },
  menutextcolor: { type: String, default: 'gray-300' },
  menuround: { type: String, default: 'md' },
  menuposition: { type: String, default: 'left-1/2 -translate-x-1/2' },
  activebg: { type: String, default: 'white/5' },
  activetext: { type: String, default: 'white' }
})
</script>
