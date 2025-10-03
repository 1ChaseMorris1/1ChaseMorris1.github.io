<template>
  <div class="p-8 space-y-6">
    <!-- Simple -->
    <Dropdown
      label="Menu"
      :items="[
        { text: 'Profile', href: '#' },
        { text: 'Settings', href: '#' },
        { text: 'Logout', href: '#' }
      ]"
    />

    <!-- Custom look -->
    <Dropdown
      label="Custom Actions"
      bgcolor="blue-600"
      textcolor="white"
      round="lg"
      iconcolor="white"
      bgmenucolor="blue-900"
      menutextcolor="white/80"
      menuround="lg"
      menuposition="left-1/2 -translate-x-1/2"
      activebg="blue-700"
      activetext="white"
      :items="[
        { text: 'Dashboard', href: '#' },
        { text: 'Analytics', href: '#' },
        { text: 'Logout', href: '#' }
      ]"
    />
  </div>
</template>

<script setup>
import Dropdown from './Dropdown.vue'
</script>
