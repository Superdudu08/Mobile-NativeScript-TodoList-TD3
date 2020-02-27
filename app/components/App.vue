<template>
    <Page>
      <ActionBar title="Groceries">
        <ActionItem text="Add" @tap="onAddTap"></ActionItem>
      </ActionBar>
      <StackLayout>
        <GroceryList :items="items"/>
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
        items: groceryData.groceryItems
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
      }
    }
  }
</script>

<style scoped>
  ActionBar {
    background-color: red;
  }
</style>
