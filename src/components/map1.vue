<template>
    <div ref="map" id="map" style="height: 90vh; width: 90vw;"></div>
</template>

<script setup>
import tt from '@tomtom-international/web-sdk-maps';
import { onMounted, ref, useTemplateRef } from 'vue';


const map = useTemplateRef("map");
const mapIntance = ref(null);

const initTomTom = () => {
    tt.setProductInfo("Fero", "1.1")
    mapIntance.value = ref(tt.map({
        key: import.meta.env.VITE_TOMTOM_API_KEY,
        container: map.value,
        center: [15.4, 53.0], // take it as a prop
        zoom: 3, // take it as a prop
    }));
}

onMounted(() => {
    initTomTom();
});

</script>