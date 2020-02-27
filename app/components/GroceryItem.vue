<template>
    <GridLayout columns="140,*,40" rows="60">
        <Label col="0" :text="statusText" @tap="onDoneTap"></Label>
        <Label col="1" class="item-name" :class="{ 'line-through' : groceryItem.done }" :text="groceryItem.name" @tap="onNameTap"></Label>
        <Label col="2" @tap="onDeleteTap" text="🗑️"></Label> 
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
        },
        onDeleteTap: function() {
            this.$emit('deleteTap', this.groceryItem);
        }
    }
}
</script>

<style lang="scss" scoped>
page {
    label {
        color:black;
    }
    .line-through {
        text-decoration: line-through;
    }
}
label {
    background-color: rgb(206, 188, 188);
}

.fas {
    font-family: "Font Awesome 5 Free", "fa-solid-900";
    font-weight: 900;
  }
</style>