<template>
    <Page>
        <StackLayout>
            <Label text="Delete this task ?"></Label>
            <Button text="No" @tap="onNoTap"></Button>
            <Button text="Yes" @tap="onYesTap"></Button>
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
        onYesTap: function() {
            this.$modal.close(true);
        },
        onNoTap: function(){
            this.$modal.close(false);
        }
    }

}
</script>

<style lang="scss" scoped>

StackLayout {
    width:100%;
    padding:30px;
}
label {
    text-align:center;
    padding:20px;
}

button {
    background-color: rgb(228, 201, 201);
    border-radius:5%;
    margin-bottom:30px;
}
</style>