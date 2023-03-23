<script lang="ts" setup>
import { ref } from "vue";
const show1 = ref(false);
const show2 = ref(false);
// const show3 =ref(false);

const deviceInfomations = ref([
  {
    //
    asNumber: "65534",
    rd: "65534:100",
    importPolicy: "SET-C10",
    exportPolicy: "SET-C10",

    interface: [
      {
        "bundleEther1.100": {
          //Interface名（可変）
          description: "to-Node11",
          ipAddress: [" 192.168.11.1/24"],
        },
        "gigabitEthernet0/0/0/0": {
          //Interface名（可変）
          description: "to - Node21",
          ipAddress: [
            { address: "192.168.21.1/24" },
            { address: "192.168.22.1/29", secondary: true },
            { address: "192.168.23.1/29", secondary: true },
          ],
        },
      },
    ],
    routing: {
      bgpNeighbor: [
        //固定
        { address: "192.168.21.2", as: "18000" },
        { address: "192.168.21.3", as: "18000" },
      ],
    },
    // srPolicy: [
    //     { endpoint: 'ACR11', color: '10' },
    //     { endpoint: 'ACR12', color: '10' },
    //     { endpoint: 'WSE12', color: '10' }
    // ]
  },
]);
</script>

<template>
  <v-card
    class="mx-auto"
    style="width: 500px"
    v-for="item in deviceInfomations"
  >
    <!-- General Infomation start -->
    <v-card-title> General Infomation </v-card-title>

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
    <!-- General Infomation end -->

    <!-- Interface start -->
    <v-card-actions style="padding: 0px">
      <v-card-title> Interface </v-card-title>
      <v-spacer></v-spacer>

      <v-btn
        :icon="show1 ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="show1 = !show1"
      >
      </v-btn>
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

      <v-btn
        :icon="show2 ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="show2 = !show2"
      >
      </v-btn>
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
