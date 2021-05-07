<template>
  <div>
    <v-list-group
      v-if="item.items !== undefined"
      v-model="item.active"
      no-action
      :sub-group="isSubGroup"
      :class="isSubGroup ? 'right-icon' : ''"
    >
      <template v-slot:activator>
        <v-list-item-content>
          <v-list-item-title>
            <v-icon>{{ item.icon }}</v-icon>{{ item.title }}
          </v-list-item-title>
        </v-list-item-content>
      </template>
      <template v-for="subItem in item.items">
        <list-item
          :key="subItem.title"
          :item="subItem"
          :is-sub-group="true"
        />
      </template>
    </v-list-group>
    <v-list-item
      v-else
      link
      router
      :to="item.to"
    >
      <v-list-item-avatar left>
        <v-icon>{{ item.icon }}</v-icon>
      </v-list-item-avatar>
      <v-list-item-content>
        <v-list-item-title v-text="item.title" />
      </v-list-item-content>
    </v-list-item>
  </div>
</template>

<script>
  export default {
    name: 'MyListItem',
    props: ['item', 'isSubGroup'],
    components: {
      ListItem: () => import('./MyListItem.vue'),
    },
  }
</script>
<style>
 .right-icon .v-list-group__header {
  display: flex !important;
  flex-direction: row-reverse !important;
 }
</style>
