<template>
    <Page>

        <WebView v-if="estateName === 'Festival City'"
            src="https://leafletapi.mtchoy.now.sh/index.html?lat=22.36&lng=114.17&zoom=17&markerLat=22.369272&markerLng=114.174345&markerTitle=Festival%20City&locate=true" />

        <WebView v-else-if="estateName === 'City One Shatin'"
            src="https://leafletapi.mtchoy.now.sh/index.html?lat=22.38&lng=114.20&zoom=17&markerLat=22.386389&markerLng=114.203889&markerTitle=City%20One%20Shatin&locate=true" />

        <WebView v-else-if="estateName === 'Tin Ma Court'"
            src="https://leafletapi.mtchoy.now.sh/index.html?lat=22.34&lng=114.18&zoom=17&markerLat=22.342980&markerLng=114.187150&markerTitle=Tin%20Ma%20Court&locate=true" />

    </Page>
</template>

<script>
    export default {
        props: ["estateName", "$delegate"],
        data() {
            return {};
        }
    };
</script>

<style>
</style>