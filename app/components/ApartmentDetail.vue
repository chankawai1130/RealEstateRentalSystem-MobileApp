<template>
    <Page>

        <ScrollView orientation="vertical">
            <StackLayout orientation="vertical" margin="10">
                <Image :src="selectedApartment.image" height="300"
                    stretch="aspectFill" />
                <Label :text="selectedApartment.title" class="h1" />


                <Label :text="'Estate: ' + selectedApartment.name"
                    margin="10" />
                <Label :text="'Bedrooms: ' + selectedApartment.bedrooms"
                    margin="10" />
                <Label :text="'Rent: $' + selectedApartment.rent"
                    margin="10" />
                <Label :text="'Tenants: ' + selectedApartment.tenants"
                    margin="10" />
                <Label
                    :text="'Area: ' + selectedApartment.area + ' square feet'"
                    margin="10" />

                <Button text="Address" @tap="onAddressTap(selectedApartment)"
                    class="btn btn-primary btn-rounded-lg" />
                <Button text="Move-in" @tap="onMoveInTap"
                    class="btn btn-primary btn-rounded-lg" />
            </StackLayout>
        </ScrollView>

    </Page>
</template>

<script>
    import Address from "./Address";
    export default {
        props: ["selectedApartment", "$delegate"],
        methods: {
            async onAddressTap(args) {
                console.log("Address button was pressed");
                this.$navigateTo(Address, {
                    transition: {},
                    transitionIOS: {},
                    transitionAndroid: {},
                    props: {
                        estateName: args.name,
                        $delegate: this
                    }
                });
            },

            async onMoveInTap() {
                console.log("Move-in button was pressed");
                var result = await confirm({
                    title: "Are you sure?",
                    message: "to move in this apartment?",
                    okButtonText: "Yes",
                    cancelButtonText: "No"
                });
                if (result) {
                    await confirm({
                        title: "Move-in successfuy.",
                        okButtonText: "OK"
                    });
                } 
            }
        },
        data() {
            return {};
        }
    };
</script>

<style>
</style>