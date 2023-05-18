<script>
    export default {
        name: "Input",
        props: {
            inputType: String,
            inputID: String,
            labelFor: String,
            labelContent: String
        },
        data(){
            return{
                inputValue: ''
            }
        },
        methods: {
            emitValue(){
                this.$emit('input-value', this.inputValue)
            }
        }
    }
</script>

<template>
    <fieldset>
        <label :for="labelFor">{{labelContent}}</label>
        <input :type="inputType" :id="inputID" v-model="inputValue" @input="emitValue">
    </fieldset>
</template>