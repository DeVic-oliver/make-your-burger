<script>
    export default {
        name: "Select",
        props: {
            selectID: String,
            selectName: String,
            labelFor: String,
            labelContent: String,
            selectOptions: {
                type: Object,
                required: true
            }
        }
    }
</script>

<template>
    <fieldset>
        <label :for="labelFor">{{labelContent}}</label>
        <select :name="selectName" :id="selectID">
            <option value="" disabled>--Choose--</option>
            <option :v-for="option in selectOptions" :value="option.optionValue"> {{option.optionContent}} </option>
        </select>
    </fieldset>
</template>
