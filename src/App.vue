<template>
    <div class="flex flex-col justify-between w-full h-screen bg-gray-700">
        <MainHeader title="Currency Converter" />
        <MainBody />
    </div>
</template>

<script>
import MainHeader from "./components/MainHeader.vue";
import MainBody from "./components/MainBody.vue";
export default {
    components: {
        MainHeader,
        MainBody,
    },
};
</script>
