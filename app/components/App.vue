<template>
    <Page>
      <ActionBar title="Groceries">
        <ActionItem text="Add" @tap="onAddTap"></ActionItem>
        <ActionItem text="Filter" @tap="toggleFilter"></ActionItem>
      </ActionBar>
      <StackLayout>
        <GroceryList :items="items" :filterDone="filterDone"/>
      </StackLayout>
    </Page>
</template>

<script > 
  import GroceryList from "./GroceryList";
  import groceryData from '../grocery-data.json';
  import AddItem from './AddItem';

  export default {
    components: {GroceryList},
    data() {
      return {
        items: groceryData.groceryItems,
        filterDone: false
      }
    },
    methods: {
      onAddTap() {
        const newId= new Date().getTime();
        this.$showModal(AddItem, {
          props: {
            id: newId
          }
        }).then( newItem => {
          if(newItem) {
            this.items.push(newItem);
          }
        })
      },
      toggleFilter() {
        this.filterDone = !this.filterDone;
      }
    }
  }
</script>

<style scoped>
  ActionBar {
    background-color: rgb(228, 201, 201);
  }
</style>
