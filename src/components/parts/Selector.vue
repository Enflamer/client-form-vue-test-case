<template>
    <div class="selector">
        <label :for="tag">{{ title }}:</label>
        <select :multiple="multiple" :name="tag">
            <option v-for="option in options" :key="option">
                {{ option }}
            </option>
        </select>
    </div>
</template>

<script>
export default {
    name: "Selector",
    props: {
        title: {
            type: String,
            require: true,
        },
        tag: {
            type: String,
            require: true,
        },
        options: {
            type: Array,
            require: true,
        },
        multiple: {
            type: Boolean,
        },
    },
 
};
</script>
<style lang="scss">
.selector {
    display: flex;
    flex-direction: column;
    width: calc(50% - 20px);
}
</style>
