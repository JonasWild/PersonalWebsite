<template>
  <div class='root_my_list_item'>
    <v-list-group
      v-if="item.items !== undefined"
      v-model="item.active"
      no-action
      :sub-group="isSubGroup"
      :class="isSubGroup ? 'right-icon' : 'main_item'"
      :id="isSubGroup ? 'parent_group_list_item' : 'main_item'"
    >
      <template
        v-slot:activator
        class='parent_list_children_container'
      >
        <v-list-item-content
          class='my_list_item'
          id='parent_group_list_item_content'
        >
          <v-list-item-title
            id='parent_group_list_item_title'
            v-text="item.title"
          />
        </v-list-item-content>
      </template>
      <template
        v-for="subItem in item.items"
        class='list_children_container_wrapper'
      >
        <list-item
          :key="subItem.title"
          :item="subItem"
          :is-sub-group="true"
          class='list_children_container'
        />
      </template>
    </v-list-group>
    <v-list-item
      v-else
      link
      router
      :to="item.to"
      id='child_list_item'
    >
      <v-list-item-content
        class='my_list_item'
        id='child_group_list_item_content'
      >
        <v-list-item-title
          v-text="item.title"
          id='child_group_list_item_title'
        />
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
<style lang="sass">
  .right-icon .v-list-group__header
    display: flex !important
    flex-direction: row-reverse !important

  .v-list-group.v-list-group--active.v-list-group--no-action.primary--text.main_item
    -moz-box-shadow:    inset 0 0 10px #000000
    -webkit-box-shadow: inset 0 0 10px #000000
    box-shadow:         inset 0 0 10px #000000
    color: grey !important

  .root_my_list_item
    color: grey !important

    .root_my_list_item
      color: grey !important

  #main_item
    background-color: transparent

  #parent_group_list_item
    background-color: black
    border-radius: 0px 0px 10px 10px
    color: grey !important

  #parent_group_list_icon
    padding-right: 15px

  #parent_group_list_item_content
    padding-top: 22px
    padding-bottom: 22px

  #parent_group_list_item_title
    font-size: 17px
    font-weight: 400
    padding-top: 5px
    padding-left: 10px
    padding-right: 10px

  #child_list_item
    text-align: center
    height: 15px

  #child_group_list_item_content

  #child_group_list_item_title
    font-size: 13px
    font-weight: 300

  #child_group_list_item_icon
    height: 15px
    width: 15px

  .my_list_item

</style>
