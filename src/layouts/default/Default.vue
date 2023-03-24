<script lang="ts" setup>
  // import DefaultBar from './AppBar.vue'
  import DefaultView from './View.vue'
  // import SideBar from '@/components/DeviceInfoComponent.vue'
  import DeviceInfoComponent from '@/components/DeviceInfoComponent.vue'

  const deviceInfo = [
    {
      asNumber: '65534',
      rd: '65534:100',
      importPolicy: 'SET-C10',
      exportPolicy: 'SET-C10',
      interface: [
        {
          name: 'bundleEther1.100',
          detail: {
            description: 'to-Node11',
            ipAddress: [' 192.168.11.1/24'],
          },
        },
        {
          name: 'gigabitEthernet0/0/0/0',
          detail: {
            description: 'to - Node21',
            ipAddress: [
              { address: '192.168.21.1/24' },
              { address: '192.168.22.1/29', secondary: true },
              { address: '192.168.23.1/29', secondary: true },
            ],
          },
        },
      ],
      routing: {
        bgpNeighbor: [
          { address: '192.168.21.2', as: '18000' },
          { address: '192.168.21.3', as: '18000' },
        ],
      },
    },
    {
      asNumber: '65534',
      rd: '65534:100',
      importPolicy: 'SET-C10',
      exportPolicy: 'SET-C10',
      interface: [
        {
          name: 'bundleEther1.100',
          detail: {
            description: 'to-Node11',
            ipAddress: [' 192.168.11.1/24'],
          },
        },
        {
          name: 'gigabitEthernet0/0/0/0',
          detail: {
            description: 'to - Node21',
            ipAddress: [
              { address: '192.168.21.1/24' },
              { address: '192.168.22.1/29', secondary: true },
              { address: '192.168.23.1/29', secondary: true },
            ],
          },
        },
      ],
      routing: {
        bgpNeighbor: [
          { address: '192.168.21.2', as: '18000' },
          { address: '192.168.21.3', as: '18000' },
        ],
      },
    },
  ]
</script>

<template>
  <v-app>
    <!-- <default-bar /> -->
    <DeviceInfoComponent :device-info="deviceInfo" />
    <default-view />
  </v-app>
</template>
