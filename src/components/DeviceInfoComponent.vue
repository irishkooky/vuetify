<script setup lang="ts">
  import { ref, withDefaults } from 'vue'
  const show1 = ref(false)
  const show2 = ref(false)
  // const show3 =ref(false);
  const props = withDefaults(
    defineProps<{
      deviceInfo:
        | {
            asNumber: string
            rd: string
            importPolicy: string
            exportPolicy: string
            interface: {
              name: string
              detail: {
                description: string
                ipAddress: string[]
              }
            }[]
            routing: {
              bgpNeighbor: {
                address: string
                as: string
              }[]
            }
          }[]
        | null
    }>(),
    {
      deviceInfo: null,
    }
  )
</script>

<template>
  <v-card class="mx-auto" style="width: 500px" v-for="(item, deviceIndex) in props.deviceInfo" :key="deviceIndex">
    <!-- General Information start -->
    <v-card-title>{{ item }}</v-card-title>

    <v-table fixed-header style="padding-left: 16px; padding-right: 16px">
      <tbody>
        <tr>
          <td>AS Number</td>
          <td>{{ item.asNumber }}</td>
        </tr>
        <v-divider style="border-top-width: 0px"></v-divider>

        <tr>
          <td>RD</td>
          <td>{{ item.rd }}</td>
        </tr>
        <v-divider style="border-top-width: 0px"></v-divider>

        <tr>
          <td>Import Policy</td>
          <td>{{ item.importPolicy }}</td>
        </tr>
        <v-divider style="border-top-width: 0px"></v-divider>

        <tr>
          <td>Export Policy</td>
          <td>{{ item.exportPolicy }}</td>
        </tr>
      </tbody>
    </v-table>
    <!-- General Information end -->

    <!-- Interface start -->
    <v-card-actions style="padding: 0px">
      <v-card-title> Interface </v-card-title>
      <v-spacer></v-spacer>

      <v-btn :icon="show1 ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="show1 = !show1"> </v-btn>
    </v-card-actions>

    <v-card elevation="0" style="padding-left: 16px; padding-right: 16px">
      <div v-show="show1">
        <div>
          <v-card-title> BundleEther1.100 </v-card-title>

          <v-table fixed-header style="padding-left: 16px; padding-right: 16px">
            <tbody>
              <tr>
                <td>Description</td>
                <td>{{ item.asNumber }}</td>
              </tr>
              <v-divider style="border-top-width: 0px"></v-divider>
              <tr>
                <td>IP Address</td>
                <td>{{ item.asNumber }}</td>
              </tr>
            </tbody>
          </v-table>
        </div>

        <div>
          <v-card-title> GigabitEthernet0/0/0/0 </v-card-title>

          <v-table fixed-header style="padding-left: 16px; padding-right: 16px">
            <tbody>
              <tr>
                <td>Description</td>
                <td>{{ item.asNumber }}</td>
              </tr>
              <v-divider style="border-top-width: 0px"></v-divider>
              <tr>
                <td>IP Address</td>
                <td>{{ item.asNumber }}</td>
              </tr>
            </tbody>
          </v-table>
        </div>
      </div>
    </v-card>
    <!-- Interface end -->

    <!-- Routing start -->
    <v-card-actions style="padding: 0px">
      <v-card-title> Routing </v-card-title>

      <v-spacer></v-spacer>

      <v-btn :icon="show2 ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="show2 = !show2"> </v-btn>
    </v-card-actions>

    <div v-show="show2">
      <v-table fixed-header style="padding-left: 16px; padding-right: 16px">
        <tbody>
          <tr>
            <td>{{ item.exportPolicy }}</td>
            <td>{{ item.exportPolicy }}</td>
          </tr>
        </tbody>
      </v-table>
    </div>
    <!-- Routing end -->

    <!-- SR Policy start -->
    <!-- <v-card-actions style="padding: 0px;">
        <v-card-title>
        SR Policy
        </v-card-title>
        <v-spacer></v-spacer>

        <v-btn
        :icon="show3 ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="show3 = !show3"
        >
        </v-btn>
    </v-card-actions>

        <div v-show="show3">
            <v-table
            fixed-header
            style="padding-left: 16px; padding-right: 16px;"
            >
            <tbody>
                <tr>
                    <td>SR</td>
                    <td>{{ item.srPolicy }}</td>
                </tr>
                <v-divider style="border-top-width: 0px;"></v-divider>

                <tr>
                    <td>IP Address</td>
                    <td>{{ item.interface }}</td>
                </tr>
            </tbody>
            </v-table>
        </div> -->
    <!-- SR Policy end -->
  </v-card>
</template>
