<template lang="">
    <div>
        <h2 class="general__title">О вас</h2>

        <div class="general-info">
            <Input
                class="general-info__lastname"
                :title="'Фамилия'"
                :tag="'lastName'"
                :inputType="'text'"
                :rules="{ required: true }"
                v-model="lastName"
            />
            <Input
                class="general-info__firstname"
                :title="'Имя'"
                :tag="'firstname'"
                :rules="{ required: true }"
                v-model="firstName"
            />

            <Input
                class="general-info__patronymic"
                :title="'Отчество'"
                :tag="'patronymic'"
            />

            <Input
                class="general-info__birthdate"
                :title="'Дата рождения'"
                :tag="'birhdate'"
                :inputType="'date'"
                :rules="{ required: true }"
            />

            <Input
                class="general-info__phone"
                :title="'Номер телефона'"
                :tag="'phone'"
                :rules="{ required: true, maxLengthValue: true, minLengthValue:true }"
            />

            <Input
                class="general-info__gender"
                :title="'Пол'"
                :tag="'gender'"
            />

            <Selector
                class="general-info-client-group"
                :multiple="true"
                :title="'Группа клиентов'"
                :tag="'clientGroup'"
                :options="['VIP', 'Проблемные', 'ОМС']"
            />

            <Selector
                class="general-info-client-group"
                :multiple="false"
                :title="'Лечащий врач'"
                :tag="'clientGroup'"
                :options="['Иванов', 'Захаров', 'Чернышева']"
            />

            <div>
                <label>Не отправлять СМС:</label>
                <input type="checkbox" />
            </div>
        </div>
    </div>
</template>
<script>
import Input from "./parts/Input.vue";
import Selector from "./parts/Selector.vue";
import { required } from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core";

export default {
    setup: () => ({ v$: useVuelidate() }),
    data: () => ({
        lastName: "",
        firstName: "",
        required,
    }),
    name: "GeneralInfo",
    components: {
        Input,
        Selector,
    },
};
</script>
<style lang="scss">
@import url("../style/style.scss");
.general__title {
    margin: 0 0 0 42px;
}
.general-info {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 30px;
    border: 1px solid black;

    &-client-group {
        display: flex;
    }
}
.error {
    color: red;
    font-size: 12px;
}
</style>
