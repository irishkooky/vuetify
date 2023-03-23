<template>
  <v-app>
    <!-- <default-bar /> -->
    <DeviceInfoComponent />
    <default-view />
  </v-app>
</template>

<script lang="ts" setup>
  // import DefaultBar from './AppBar.vue'
  import DefaultView from './View.vue'
  // import SideBar from '@/components/DeviceInfoComponent.vue'
  import DeviceInfoComponent from '@/components/DeviceInfoComponent.vue';
</script>
