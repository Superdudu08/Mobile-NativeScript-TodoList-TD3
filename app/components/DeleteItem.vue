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