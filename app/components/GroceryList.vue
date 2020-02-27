<template>
    <ListView for="item in items">
        <v-template>
            <GroceryItem :groceryItem="item" @doneTap="onToggleDone" @nameTap="onItemTap"></GroceryItem>
        </v-template>
    </ListView>
</template>

<script > 
    import GroceryItem from "./GroceryItem";
    import Detail from './Detail';

  export default {
    components: {GroceryItem, Detail},
    props: ['items'],
    methods: {
        onToggleDone(groceryItem) {
            const newItem = Object.assign(groceryItem, { done: !groceryItem.done});

            const idx = this.items.findIndex(i => i.id === groceryItem.id);

            this.items = Object.assign( [], this.items, { idx: newItem});
        },
        onItemTap(args) {
            this.$navigateTo(Detail, {
                props: {
                    groceryItem: args
                }
            });
        }
    }
  }
</script>

