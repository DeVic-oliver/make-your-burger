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
    },
    methods:{
        async getIngredientsFromAPI() {
            const apiURL = 'http://localhost:3000' 
            const request = await fetch(`${apiURL}/ingredientes`);
            const data = await request.json();
            this.breadOptions = data.paes;
            this.meatOptions = data.carnes;
            this.addons = data.opcionais;
        }
    },
    mounted(){
        this.getIngredientsFromAPI();
    }
}
</script>

<template>
    <form action="" method="post">
        <Input input-type="text" input-ID="customer-name" input-name="customer_name" label-for="customer-name" label-content="Customer Name" />
        <Select select-ID="bread-type" select-name="bread_type" label-for="bread-type" label-content="Bread Type" :options="this.breadOptions" />
        <Select select-ID="meat-type" select-name="meat_type" label-for="meat-type" label-content="Meat Type" :options="this.meatOptions" />
        <fieldset>
            <label>Add-ons</label>
            <div v-for="addon in this.addons" :key="addon.id">
                <label :for="`${addon.id}_${addon.tipo}`">{{ addon.tipo }}</label>
                <input :id="`${addon.id}_${addon.tipo}`" type="checkbox" name="addon[]"  />
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