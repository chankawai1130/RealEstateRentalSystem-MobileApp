<template>
    <Page>

        <GridLayout>


            <ListView v-if="estateName === 'Festival City'"
                for="apartment in festivalCity" @itemTap="onItemTap"
                style="height:1250px">
                <v-template>
                    <FlexboxLayout flexDirection="row">
                        <Label :text="apartment.title" class="t-12"
                            style="width: 60%" />
                    </FlexboxLayout>
                </v-template>
            </ListView>

            <ListView v-if="estateName === 'Tin Ma Court'"
                for="apartment in tinMaCourt" @itemTap="onItemTap"
                style="height:1250px">
                <v-template>
                    <FlexboxLayout flexDirection="row">
                        <Label :text="apartment.title" class="t-12"
                            style="width: 60%" />
                    </FlexboxLayout>
                </v-template>
            </ListView>

            <ListView v-if="estateName === 'City One Shatin'"
                for="apartment in cityOne" @itemTap="onItemTap"
                style="height:1250px">
                <v-template>
                    <FlexboxLayout flexDirection="row">
                        <Label :text="apartment.title" class="t-12"
                            style="width: 60%" />
                    </FlexboxLayout>
                </v-template>
            </ListView>

        </GridLayout>

    </Page>
</template>

<script>
    import ApartmentDetail from "./ApartmentDetail";
    export default {
        props: ["estateName", "$delegate"],
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
            console.log("in mounted ");
            this.festivalCity = this.apartments.filter(function(a) {
                return a.name == "Festival City";
            });
            this.tinMaCourt = this.apartments.filter(function(a) {
                return a.name == "Tin Ma Court";
            });
            this.cityOne = this.apartments.filter(function(a) {
                return a.name == "City One Shatin";
            });
        },

        data() {
            return {
                countries: [{
                        name: "Australia",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/au.png"
                    },
                    {
                        name: "Belgium",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/be.png"
                    },
                    {
                        name: "Bulgaria",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/bg.png"
                    },
                    {
                        name: "Canada",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ca.png"
                    },
                    {
                        name: "Switzerland",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ch.png"
                    },
                    {
                        name: "China",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/cn.png"
                    },
                    {
                        name: "Czech Republic",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/cz.png"
                    },
                    {
                        name: "Germany",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/de.png"
                    },
                    {
                        name: "Spain",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/es.png"
                    },
                    {
                        name: "Ethiopia",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/et.png"
                    },
                    {
                        name: "Croatia",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/hr.png"
                    },
                    {
                        name: "Hungary",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/hu.png"
                    },
                    {
                        name: "Italy",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/it.png"
                    },
                    {
                        name: "Jamaica",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/jm.png"
                    },
                    {
                        name: "Romania",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ro.png"
                    },
                    {
                        name: "Russia",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/ru.png"
                    },
                    {
                        name: "United States",
                        imageSrc: "https://play.nativescript.org/dist/assets/img/flags/us.png"
                    }
                ],

                apartments: [{
                        title: "平絕同區",
                        image: "https://img.huffingtonpost.com/asset/5dcc613f1f00009304dee539.jpeg?cache=QaTFuOj2IM&ops=crop_834_777_4651_2994%2Cscalefit_720_noupscale",
                        name: "Tin Ma Court",
                        bedrooms: 2,
                        area: 550,
                        tenants: 1,
                        rent: 12000,
                        highlighted: "on"
                    },
                    {
                        title: "沙田第一城 套3房剛翻新",
                        image: "https://www.monash.vic.gov.au/files/assets/public/our-services/animals/cat-sleeps-on-couch.jpg",
                        name: "City One Shatin",
                        bedrooms: 3,
                        area: 900,
                        tenants: 5,
                        rent: 15000,
                        highlighted: "off"
                    },
                    {
                        title: "酒店式靚裝，有泳池會所",
                        image: "https://www.thoughtco.com/thmb/JhuPr0_SbnnIXiTm1PrQ5nfjdvQ=/768x0/filters:no_upscale():max_bytes(150000):strip_icc()/acat-874e4928f96e4e96bec0b1723ca5a909.jpg",
                        name: "Festival City",
                        bedrooms: 3,
                        area: 700,
                        tenants: 1,
                        rent: 18000,
                        highlighted: "on"
                    }
                ],

                estates: [{
                        name: "City One Shatin"
                    },
                    {
                        name: "Festival City"
                    },
                    {
                        name: "Tin Ma Court"
                    }
                ],

                cityOne: [],
                festivalCity: [],
                tinMaCourt: []
            };
        }
    };
</script>

<style>
</style>