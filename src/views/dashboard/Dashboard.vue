<template>
  <v-container
    id="dashboard"
    fluid
    tag="section"
  >
    <v-row>
      <v-col
        cols="12"
        lg="4"
      >
        <projectcard
          color="#8aa3b4"
          type="Bar"
          customid="vints_card"
        >
          <h4 class="card-title font-weight-light mt-2 ml-2">
            V I N T S
          </h4>

          <p class="d-inline-flex font-weight-light ml-2 mt-1">
            Flohmarkt App (Schweiz)
          </p>

          <template v-slot:actions>
            <v-icon
              class="mr-1"
              small
            >
              mdi-clock-outline
            </v-icon>
            <span class="text-caption grey--text font-weight-light">updated 10 minutes ago</span>
          </template>
        </projectcard>
      </v-col>

      <v-col
        cols="12"
        lg="4"
      >
        <projectcard
          color="#998866"
          type="Bar"
          customid="chess_card"
        >
          <h4 class="card-title font-weight-light mt-2 ml-2">
            Schach
          </h4>

          <p class="d-inline-flex font-weight-light ml-2 mt-1">
            Digitaler Trainer
          </p>

          <template v-slot:actions>
            <v-icon
              class="mr-1"
              small
            >
              mdi-clock-outline
            </v-icon>
            <span class="text-caption grey--text font-weight-light">updated 10 minutes ago</span>
          </template>
        </projectcard>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

  export default {
    name: 'DashboardDashboard',
    components: {
      Projectcard: () => import('./component/Projectcard'),
    },

    data () {
      return {
        dailySalesChart: {
          data: {
            labels: ['M', 'T', 'W', 'T', 'F', 'S', 'S'],
            series: [
              [12, 17, 7, 17, 23, 18, 38],
            ],
          },
          options: {
            lineSmooth: this.$chartist.Interpolation.cardinal({
              tension: 0,
            }),
            low: 0,
            high: 50, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
            chartPadding: {
              top: 0,
              right: 0,
              bottom: 0,
              left: 0,
            },
          },
        },
        dataCompletedTasksChart: {
          data: {
            labels: ['12am', '3pm', '6pm', '9pm', '12pm', '3am', '6am', '9am'],
            series: [
              [230, 750, 450, 300, 280, 240, 200, 190],
            ],
          },
          options: {
            lineSmooth: this.$chartist.Interpolation.cardinal({
              tension: 0,
            }),
            low: 0,
            high: 1000, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
            chartPadding: {
              top: 0,
              right: 0,
              bottom: 0,
              left: 0,
            },
          },
        },
        emailsSubscriptionChart: {
          data: {
            labels: ['Ja'],
            series: [
              [542],

            ],
          },
          options: {
            axisX: {
              showGrid: false,
            },
            low: 0,
            high: 1000,
            chartPadding: {
              top: 0,
              right: 5,
              bottom: 0,
              left: 0,
            },
          },
          responsiveOptions: [
            ['screen and (max-width: 640px)', {
              seriesBarDistance: 5,
              axisX: {
                labelInterpolationFnc: function (value) {
                  return value[0]
                },
              },
            }],
          ],
        },
        headers: [
          {
            sortable: false,
            text: 'ID',
            value: 'id',
          },
          {
            sortable: false,
            text: 'Name',
            value: 'name',
          },
          {
            sortable: false,
            text: 'Salary',
            value: 'salary',
            align: 'right',
          },
          {
            sortable: false,
            text: 'Country',
            value: 'country',
            align: 'right',
          },
          {
            sortable: false,
            text: 'City',
            value: 'city',
            align: 'right',
          },
        ],
        items: [
          {
            id: 1,
            name: 'Dakota Rice',
            country: 'Niger',
            city: 'Oud-Tunrhout',
            salary: '$35,738',
          },
          {
            id: 2,
            name: 'Minerva Hooper',
            country: 'Curaçao',
            city: 'Sinaai-Waas',
            salary: '$23,738',
          },
          {
            id: 3,
            name: 'Sage Rodriguez',
            country: 'Netherlands',
            city: 'Overland Park',
            salary: '$56,142',
          },
          {
            id: 4,
            name: 'Philip Chanley',
            country: 'Korea, South',
            city: 'Gloucester',
            salary: '$38,735',
          },
          {
            id: 5,
            name: 'Doris Greene',
            country: 'Malawi',
            city: 'Feldkirchen in Kārnten',
            salary: '$63,542',
          },
        ],
        tabs: 0,
        tasks: {
          0: [
            {
              text: 'Sign contract for "What are conference organizers afraid of?"',
              value: true,
            },
            {
              text: 'Lines From Great Russian Literature? Or E-mails From My Boss?',
              value: false,
            },
            {
              text: 'Flooded: One year later, assessing what was lost and what was found when a ravaging rain swept through metro Detroit',
              value: false,
            },
            {
              text: 'Create 4 Invisible User Experiences you Never Knew About',
              value: true,
            },
          ],
          1: [
            {
              text: 'Flooded: One year later, assessing what was lost and what was found when a ravaging rain swept through metro Detroit',
              value: true,
            },
            {
              text: 'Sign contract for "What are conference organizers afraid of?"',
              value: false,
            },
          ],
          2: [
            {
              text: 'Lines From Great Russian Literature? Or E-mails From My Boss?',
              value: false,
            },
            {
              text: 'Flooded: One year later, assessing what was lost and what was found when a ravaging rain swept through metro Detroit',
              value: true,
            },
            {
              text: 'Sign contract for "What are conference organizers afraid of?"',
              value: true,
            },
          ],
        },
        list: {
          0: false,
          1: false,
          2: false,
        },
      }
    },

    methods: {
      complete (index) {
        this.list[index] = !this.list[index]
      },
    },
  }
</script>

<style lang="sass">
  #chess_card
    background-image: url('data:image/svg+xml;base64,PHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHZpZXdCb3g9IjAgMCA4MDAgODAwIj4NCjxnIGlkPSJicm93bi1ib2FyZCI+DQo8ZyBpZD0iTGlnaHQiIGZpbGw9IiNkZWUzZTYiPg0KPHJlY3Qgd2lkdGg9IjgwMCIgaGVpZ2h0PSI4MDAiLz4NCjwvZz4NCjxnIGlkPSJGcmFtZSIgZmlsbD0ibm9uZSI+DQo8cmVjdCB3aWR0aD0iODAwIiBoZWlnaHQ9IjgwMCIvPg0KPC9nPg0KPGcgaWQ9IkRhcmsiIGZpbGw9IiM4Y2EyYWQiPg0KPGcgaWQ9InJheiI+DQo8ZyBpZD0iZHZhIj4NCjxnIGlkPSJ0cmkiPg0KPHJlY3QgeD0iMTAwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjEwMCIvPg0KPHJlY3QgeD0iMzAwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjEwMCIvPg0KPHJlY3QgeD0iNTAwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjEwMCIvPg0KPHJlY3QgeD0iNzAwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjEwMCIvPg0KPC9nPg0KPHVzZSB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTAwLDEwMCkiIHhsaW5rOmhyZWY9IiN0cmkiLz4NCjwvZz4NCjx1c2UgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMCwyMDApIiB4bGluazpocmVmPSIjZHZhIi8+DQo8L2c+DQo8dXNlIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAsNDAwKSIgeGxpbms6aHJlZj0iI3JheiIvPg0KPC9nPg0KPC9nPg0KPC9zdmc+')
    background-color: transparent !important
    border-color: transparent !important
    height: 150px !important
    width: 150px !important
    min-width: max-content
    background-repeat: no-repeat
    background-size: cover
    background-position: center

  #vints_card
    background-image: url('https://vintblobstorage.blob.core.windows.net/imagecontainer/logo.png')
    background-color: transparent !important
    border-color: transparent !important
    height: 150px !important
    width: 150px !important
    min-width: max-content
    background-repeat: no-repeat
    background-size: cover
    background-position: center
</style>
