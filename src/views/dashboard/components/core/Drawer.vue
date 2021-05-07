<template>
  <v-navigation-drawer
    id="core-navigation-drawer"
    v-model="drawer"
    :dark="barColor !== 'rgba(228, 226, 226, 1), rgba(255, 255, 255, 0.7)'"
    :expand-on-hover="expandOnHover"
    :right="$vuetify.rtl"
    mobile-break-point="960"
    app
    width="260"
    v-bind="$attrs"
    color="#111"
  >
    <div
      id="nav_header_container"
      dense
      nav
    >
      <div id="profil_image" />

      <div id="profil_text_container">
        <div
          class="text-h3"
          style="text-align: center;"
          v-text="profile.title"
        />
        <a
          href="mailto:vints.switzerland@gmail.com"
          class="text-h5"
          style="color: #999999;     text-align: center;"
        >
          jonas.wild2@hotmail.de
        </a>
      </div>
    </div>

    <v-divider class="mb-2" />

    <v-list
      expand
      nav
    >
      <div />

      <template>
        <div>
          <v-list>
            <my-list-item
              v-for="item in items"
              :key="item.title"
              :item="item"
            />
          </v-list>
        </div>
      </template>
      <div />
    </v-list>
  </v-navigation-drawer>
</template>

<script>
  // Utilities
  import {
    mapState,
  } from 'vuex'

  export default {
    name: 'DashboardCoreDrawer',
    components: {
      MyListItem: () => import('../../component/MyListItem'),
    },
    props: {
      expandOnHover: {
        type: Boolean,
        default: false,
      },
    },

    data: () => ({
      items: [
        {
          icon: 'mdi-view-dashboard',
          title: 'Projekte',
          to: '/',
          items: [
            {
              icon: 'mdi-account',
              title: 'V I N T S',
              to: '/projects/vints',
            },
            {
              icon: 'mdi-account',
              title: 'Schach',
              to: '/projects/chess',
            },
          ],
        },
        {
          icon: 'mdi-account',
          title: 'Über mich',
          to: '/pages/user',
        },
      ],
    }),

    computed: {
      ...mapState(['barColor', 'barImage']),
      drawer: {
        get () {
          return this.$store.state.drawer
        },
        set (val) {
          this.$store.commit('SET_DRAWER', val)
        },
      },
      computedItems () {
        return this.items.map(this.mapItem)
      },
      profile () {
        return {
          avatar: true,
          title: this.$t('avatar'),
        }
      },
    },

    methods: {
      mapItem (item) {
        return {
          ...item,
          children: item.children ? item.children.map(this.mapItem) : undefined,
          title: this.$t(item.title),
        }
      },
    },
  }
</script>

<style lang="sass">
  @import '~vuetify/src/styles/tools/_rtl.sass'

  #profil_text_container
    margin: 30px
    color: white

  #nav_header_container
    display: flex
    justify-content: center
    flex-direction: column
    align-items: center

  #profil_image
    background-image: url('https://vintblobstorage.blob.core.windows.net/imagecontainer/AboutJonas.jpg')
    background-color: transparent !important
    border-color: transparent !important
    height: 150px !important
    width: 150px !important
    border-radius: 75px
    margin-top: 25px
    min-width: max-content
    background-repeat: no-repeat
    background-size: cover
    background-position: center

  #core-navigation-drawer
    .v-list-group__header.v-list-item--active:before
      opacity: .24

    .v-list-item
      &__icon--text,
      &__icon:first-child
        justify-content: center
        text-align: center
        width: 20px

        +ltr()
          margin-right: 24px
          margin-left: 12px !important

        +rtl()
          margin-left: 24px
          margin-right: 12px !important

    .v-list--dense
      .v-list-item
        &__icon--text,
        &__icon:first-child
          margin-top: 10px

    .v-list-group--sub-group
      .v-list-item
        +ltr()
          padding-left: 8px

        +rtl()
          padding-right: 8px

      .v-list-group__header
        +ltr()
          padding-right: 0

        +rtl()
          padding-right: 0

        .v-list-item__icon--text
          margin-top: 19px
          order: 0

        .v-list-group__header__prepend-icon
          order: 2

          +ltr()
            margin-right: 8px

          +rtl()
            margin-left: 8px
</style>
