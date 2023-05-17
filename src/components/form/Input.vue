<script>
    export default {
        name: "Input",
        props: {
            inputType: String,
            inputID: String,
            inputName: String,
            labelFor: String,
            labelContent: String
        }
    }
</script>

<template>
    <fieldset>
        <label :for="labelFor">{{labelContent}}</label>
        <input :type="inputType" :name="inputName" :id="inputID">
    </fieldset>
</template>