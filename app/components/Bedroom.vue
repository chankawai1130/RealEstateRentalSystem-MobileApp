<template>
    <Page>
        <GridLayout>

            <ListView v-if="numberOfBedroom <= 2"
                for=" apartment in twoBedrooms " @itemTap=" onItemTap "
                style=" height:1250px ">
                <v-template>
                    <FlexboxLayout flexDirection=" row ">
                        <Label :text=" apartment.title " class=" t-12 "
                            style=" width: 60% " />
                        <Label :text=" apartment.name" class=" body "
                            style=" width: 60% " />
                    </FlexboxLayout>
                </v-template>
            </ListView>

            <ListView v-if="numberOfBedroom >= 3"
                for=" apartment in threeBedrooms " @itemTap=" onItemTap "
                style=" height:1250px ">
                <v-template>
                    <FlexboxLayout flexDirection=" row ">
                        <Label :text=" apartment.title " class=" t-12 "
                            style=" width: 60% " />
                        <Label :text=" apartment.name" class=" body "
                            style=" width: 60% " />
                    </FlexboxLayout>
                </v-template>
            </ListView>

        </GridLayout>
    </Page>
</template>

<script>
    import ApartmentDetail from "./ApartmentDetail";
    export default {
        props: ["numberOfBedroom", " $delegate "],
        methods: {
            onItemTap: function(args) {
                console.log("Item with index: " + args.index + " tapped");
                console.log("Apartment selected:" + args.item.name); 
                this.$navigateTo(ApartmentDetail, { 
                    transition: {}, 
                    transitionIOS: {}, 
                    transitionAndroid: {},
                    props: {
                        selectedApartment: args.item,
                        $delegate: this
                    }
                });
        }
    },

    mounted() {
            console.log(" in mounted ");
            this.twoBedrooms = this.apartments.filter(function(a) {
                return a.bedrooms <= 2;
            });
            this.threeBedrooms = this.apartments.filter(function(a) {
                return a.bedrooms >= 3;
            });
        },

        data() {
            return {
                apartments: [{
                        title: " 平絕同區 ",
                        image: "https://img.huffingtonpost.com/asset/5dcc613f1f00009304dee539.jpeg?cache=QaTFuOj2IM&ops=crop_834_777_4651_2994%2Cscalefit_720_noupscale ",
                        name: " Tin Ma Court ",
                        bedrooms: 2,
                        area: 550,
                        tenants: 1,
                        rent: 12000,
                        highlighted: " on "
                    },
                    {
                        title: " 沙田第一城 套3房剛翻新 ",
                        image: "https://www.monash.vic.gov.au/files/assets/public/our-services/animals/cat-sleeps-on-couch.jpg ",
                        name: " City One Shatin ",
                        bedrooms: 3,
                        area: 900,
                        tenants: 5,
                        rent: 15000,
                        highlighted: " off "
                    },
                    {
                        title: " 酒店式靚裝，有泳池會所 ",
                        image: "https://www.thoughtco.com/thmb/JhuPr0_SbnnIXiTm1PrQ5nfjdvQ=/768x0/filters:no_upscale():max_bytes(150000):strip_icc()/acat-874e4928f96e4e96bec0b1723ca5a909.jpg ",
                        name: " Festival City ",
                        bedrooms: 3,
                        area: 700,
                        tenants: 1,
                        rent: 18000,
                        highlighted: " on "
                    }
                ],

                twoBedrooms: [],
                threeBedrooms: []
            };
        }
    };
</script>

<style>
</style>