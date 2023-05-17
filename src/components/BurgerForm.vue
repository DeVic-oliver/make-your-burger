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
            breadOptions: [],
            meatOptions: [],
            addons: [],
        }
    }
}
</script>

<template>
    <form action="" method="post">
        <Input input-type="text" input-ID="customer-name" input-name="customer_name" label-for="customer-name" label-content="Customer Name" />
        <Select select-ID="bread-type" select-name="bread_type" label-for="bread-type" label-content="Bread Type" :options="this.breadOptions" />
        <Select select-ID="meat-type" select-name="meat_type" label-for="meat-type" label-content="Meat Type" :options="this.meatOptions" />
        <fieldset>
            <label for="">Add-ons</label>
            <div>
                <!-- Checkbox iteration -->
            </div>
        </fieldset>
        <button type="submit">Order your burger</button>
    </form>
</template>

<style scoped>
    form{
        max-width: 350px;
        widows: 100%;
        margin: 30px auto;
    }
</style>