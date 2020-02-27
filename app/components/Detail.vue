<template>
    <Page>
        <StackLayout>
            <Button text="Go back" @tap="onBackTap"></Button>
            <Label :text="groceryItem.name"></Label>
            <Button :text="statusText" @tap='toggle'></Button>
            <Button text="Delete" v-if="groceryItem.done" @tap="onDeleteTap"></Button>
        </StackLayout>
    </Page>
</template>

<script>

  import DeleteItem from './DeleteItem';

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
           this.groceryItem.done = !this.groceryItem.done;
        },
        onBackTap : function() {
            this.$navigateBack();
        },
        onDeleteTap: function() {
            this.$showModal(DeleteItem).then( validate => {
                if(validate) {
                    this.groceryItem.deleted = true;
                    this.$navigateBack();
                }
            })
        }
    }

}
</script>