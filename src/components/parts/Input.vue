<template>
    <div class="input">
        <label :for="tag">{{ title }}:</label>
        <input
            :type="inputType"
            :name="tag"
            @input="$emit('update:modelValue', $event.target.value)"
            v-model="v$.text.$model"
        />
        <span class="error" v-for="error of v$.text.$errors" :key="error.$uid">
            Поле не может быть пустым
        </span>
    </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required, minLength, maxLength } from "@vuelidate/validators";

export default {
    setup: () => ({ v$: useVuelidate() }),
    props: {
        title: {
            type: String,
            require: true,
        },
        tag: {
            type: String,
            require: true,
        },
        inputType: {
            type: String,
            require: true,
        },
        rules: {
            type: Object,
            default: () => ({}),
        },
    },
    data() {
        return {
            text: this.rules.minLengthValue ? "7" : "",
        };
    },
    validations() {
        return {
            text: {
                required: this.rules.required ? required : false,
                minLengthValue: this.rules.minLengthValue
                    ? minLength(11)
                    : false,
                maxLengthValue: this.rules.maxLengthValue
                    ? maxLength(11)
                    : false,
            },
        };
    },
};
</script>

<style lang="scss">
.input {
    width: calc(50% - 30px);
    margin-bottom: 20px;

    input {
        width: 100%;
        padding: 5px 0;
    }
}
.error {
    display: block;
    position: absolute;
}
</style>
