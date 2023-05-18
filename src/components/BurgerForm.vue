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
            order: {
                customer_name: '',
                bread: '',
                meat: '',
            },
            breadOptions: [],
            meatOptions: [],
            addonsOptions: [],
        }
    },
    methods:{
        async getIngredientsFromAPI() {
            const request = await this.fetchAPI('ingredientes');
            const data = await request.json();
            this.breadOptions = data.paes;
            this.meatOptions = data.carnes;
            this.addonsOptions = data.opcionais;
        },
        async sendRequest(e){
            e.preventDefault();
            
            const dataToSend = {
                customer: this.order.customer_name,
                bread: this.order.bread,
                meat: this.order.meat
            }

            const dataJson = JSON.stringify(dataToSend);

            const request = await this.fetchAPI('burgers', {
                method: 'POST',
                headers: { 'Content-Type' : 'application/json' },
                body: dataJson
            });

            const response = await request.json();
            console.log(response); 
            
        },
        fetchAPI(uri = '', params = {}){
            const apiURL = 'http://localhost:3000/' + uri; 
            return fetch(apiURL, params);
        },
    },
    mounted(){
        this.getIngredientsFromAPI();
    }
}
</script>

<template>
    <form action="" method="post" @submit="sendRequest">
        <Input @input-value="this.order.customer_name = $event" input-type="text" input-ID="customer-name" label-for="customer-name" label-content="Customer Name" />
        <Select @selected-option="this.order.bread = $event" select-ID="bread-type" label-for="bread-type" label-content="Bread Type" :options="this.breadOptions" />
        <Select @selected-option="this.order.meat = $event" select-ID="meat-type" label-for="meat-type" label-content="Meat Type" :options="this.meatOptions" />
        <fieldset>
            <label>Add-ons</label>
            <div v-for="addon in this.addonsOptions" :key="addon.id">
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