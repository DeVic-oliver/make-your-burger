<script>
import Input from "./form/Input.vue";
import Select from "./form/Select.vue";

export default {
    name: "BurgerForm",
    components: {
        Input,
        Select
    },
    data (){
        return{
            customer_name: '',
            bread: '',
            meat: '',
            addons: [],
            optionsaa: { optionValue: "zap", optionContent: "sharapova" }
        }
    }
}
</script>
<template>
    <form action="" method="post">
        <Input input-type="text" input-ID="customer-name" input-name="customer_name" label-for="customer-name" label-content="Customer Name" />
        <Select select-ID="bread-type" select-name="bread_type" label-for="bread-type" label-content="Bread Type" :select-options="optionsaa" />
        <fieldset>
            <label for="">Add-ons</label>
            <div>
                <input type="checkbox" name="" id="">
                <!-- Checkbox iteration -->
            </div>
        </fieldset>
        <button type="submit">Order your burger</button>
    </form>
</template>