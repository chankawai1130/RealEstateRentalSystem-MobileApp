<template>
    <Page>

		<StackLayout orientation="vertical" class="form">
            <StackLayout orientation="vertical" margin="10">
                <TextField v-model="textFieldValue" hint="username"
                    class="input input-border" />
                <TextField v-model="textFieldValue" hint="password"
                    class="input input-border" />

                <Button text="Login" @tap="onButtonTap"
                    class="btn btn-primary btn rounded-lg" />
            </StackLayout>
        </ScrollView>

    </Page>
</template>

<script>
    export default {
        props: ["selectedProduct", "$delegate"],
        data() {
            return {};
        }
    };
</script>

<style>
</style>