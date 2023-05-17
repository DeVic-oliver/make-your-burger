<script>
    export default {
        name: "Select",
        props: {
            selectID: String,
            selectName: String,
            labelFor: String,
            labelContent: String,
            options: {
                type: Array,
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
            <option v-for="option in options" :value="option.value">{{ option.content }}</option>
        </select>
    </fieldset>
</template>
