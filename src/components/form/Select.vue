<script>
    export default {
        name: "Select",
        props: {
            selectID: String,
            labelFor: String,
            labelContent: String,
            options: {
                type: Array,
                required: true
            }
        },
        data(){
            return{
                selectedOption: ''
            }
        },
        methods:{
            emitSelection(){
                this.$emit('selected-option', this.selectedOption)
            }
        }
    }
</script>

<template>
    <fieldset>
        <label :for="labelFor">{{labelContent}}</label>
        <select :id="selectID" v-model="selectedOption" @change="emitSelection">
            <option value="" disabled>--Choose--</option>
            <option v-for="option in options" :value="option.tipo" :key="option.id">{{ option.tipo }}</option>
        </select>
    </fieldset>
</template>
