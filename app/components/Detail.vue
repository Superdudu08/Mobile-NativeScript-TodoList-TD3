<template>
    <Page>
        <ActionBar title="Details">
        </ActionBar>
        <StackLayout>
            <Label :text="todoItem.name"></Label>
            <Button text="Back" @tap="onBackTap"></Button>
            <Button :text="statusText" @tap='toggle'></Button>
            <Button text="Delete" v-if="todoItem.done" @tap="onDeleteTap"></Button>
        </StackLayout>
    </Page>
</template>

<script>

  import DeleteItem from './DeleteItem';

export default {
    props: ['todoItem'],
    data: function() {
        return {
           
        }
    },
    computed: {
        statusText: function() {
            return this.todoItem.done ? 'Done' : 'Not done';
        }
    },
    methods: {
        toggle: function() {
           this.todoItem.done = !this.todoItem.done;
        },
        onBackTap : function() {
            this.$navigateBack();
        },
        onDeleteTap: function() {
            this.$showModal(DeleteItem).then( validate => {
                if(validate) {
                    this.todoItem.deleted = true;
                    this.$navigateBack();
                }
            })
        }
    }

}
</script>

<style lang="scss" scoped>
    Button {
        background-color: rgb(228, 201, 201);
        margin-top:10px;
        margin-bottom:10px;
        width:60%;
        height:120px;
        font-size:14px;
        border-radius:5%;
    }

    Label {
        padding: 30px;
        font-size:20px;
        text-align: center;
    }

    ActionBar {
        background-color: rgb(228, 201, 201);
        color:black;
    }
</style>