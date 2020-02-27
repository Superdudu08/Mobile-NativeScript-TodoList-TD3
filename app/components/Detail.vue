<template>
    <Page>
        <StackLayout>
            <Button text="Go back" @tap="onBackTap"></Button>
            <Label :text="groceryItem.name"></Label>
            <Button :text="statusText" @tap='toggle'></Button>
        </StackLayout>
    </Page>
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
           // this.status = this.status === 0 ? 1 : 0;
           // this.$emit('toggleDone', this.groceryItem);
           this.groceryItem.done = !this.groceryItem.done;
        },
        onBackTap : function() {
            // On peut faire des trucs
            this.$navigateBack();
        }
    }

}
</script>