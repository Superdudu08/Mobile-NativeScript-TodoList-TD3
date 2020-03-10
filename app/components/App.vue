<template>
    <Page>
      <ActionBar title="TODO LIST">
        <ActionItem text="Add" @tap="onAddTap"></ActionItem>
        <ActionItem text="Filter" @tap="toggleFilter"></ActionItem>
      </ActionBar>
      <StackLayout>
        <GroceryList :items="items" :filterDone="filterDone" @updateItems="saveToLocalStorage"/>
      </StackLayout>
    </Page>
</template>

<script > 
  import GroceryList from "./GroceryList";
  import groceryData from '../grocery-data.json';
  import AddItem from './AddItem';
  import * as localstorage from 'nativescript-localstorage';


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
            this.items.unshift(newItem);
            this.saveToLocalStorage();
          }
        })
      },
      toggleFilter() {
        this.filterDone = !this.filterDone;
      },
      saveToLocalStorage() {
          localStorage.setItem("data", JSON.stringify(this.items));
      }
    },
    created: function() {
        if (localStorage.getItem("data") !== null) {
            this.items = JSON.parse(localStorage.getItem("data"));
        }
    }
  }
</script>

<style scoped>
  ActionBar {
    background-color: rgb(228, 201, 201);
    color:black;
  }
</style>
