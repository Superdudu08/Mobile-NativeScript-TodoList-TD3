<template>
    <Page>
        <StackLayout>
            <Label text="Add new task"></Label>
            <TextField v-model="name" hint="Enter task title"></TextField>
            <Button text="Save" @tap="onSaveTap"></Button>
        </StackLayout>
    </Page>
</template>

<script>
export default {
    props: ['id'],
    data: function() {
        return {
           name: ''
        }
    },
    methods: {
        onSaveTap: function() {
            const newItem = {
                id: this.id,
                name: this.name,
                done: false,
                deleted: false
            };
            this.$modal.close(newItem);
        }
    }

}
</script>

<style lang="scss" scoped>

StackLayout {
    width:80%;
}
label {
    text-align:center;
    padding:20px;
}

button {
    background-color:rgb(170, 170, 170);
    border-radius:5%;
}
</style>