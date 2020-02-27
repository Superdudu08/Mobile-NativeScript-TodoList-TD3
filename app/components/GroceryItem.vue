<template>
    <GridLayout columns="200, *">
        <Label col="0" :text="statusText" @tap="onDoneTap"></Label>
        <Label col="1" class="item-name" :class="{ 'line-through' : groceryItem.done }" :text="groceryItem.name" @tap="onNameTap"></Label>
    </GridLayout>
</template>

<script>
export default {
    props: ['groceryItem'],
    data: function() {
        return {
           
        }
    },
    computed: {
        statusText: function() {
            return this.groceryItem.done ? 'Done' : 'Not done';
        }
    },
    methods: {
        toggle: function() {
           this.$emit('toggleDone', this.groceryItem);
        },
        onDoneTap: function() {
            this.$emit('doneTap', this.groceryItem);
        },
        onNameTap: function() {
            this.$emit('nameTap', this.groceryItem);
        }
    }
}
</script>

<style lang="scss" scoped>
page {
    label {
        color:red;
    }
    .line-through {
        text-decoration: line-through;
    }
}
</style>

<style>
label {
    background-color: aqua;
}
</style>