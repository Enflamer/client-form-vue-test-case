<template lang="">
    <div class="app-container">
        <GeneralInfo />
    </div>
</template>
<script>
import GeneralInfo from "./components/GeneralInfo.vue";


export default {
    name: "App",
    components: {
        GeneralInfo,
    },
};
</script>
<style lang="scss">
#app {
    margin: 10em auto;
    padding: 0;
    width: 50%;
}
</style>
