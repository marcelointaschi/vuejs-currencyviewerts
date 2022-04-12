<template>
    <div>
        <MessageSuccess :msg="msg" v-show="msg" />
        <MessageError :msgerr="msgerr" v-show="msgerr" />
    </div>
    <div>
        <form id="cform" @submit="getConvertedValue">
            <div class="input-container">
                <label for="from">From: </label>
                <select id="from" name="from" v-model="fromconvert">
                    <option value="" selected>Select a currency</option>
                    <option v-for="currency in currencies" :key="currency.currency" :value="currency.value">{{currency.currency}}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="to">To: </label>
                <select id="from" name="from" v-model="toconvert">
                    <option value="" selected>Select a currency</option>
                    <option v-for="currency in currencies" :key="currency.currency" :value="currency.value">{{currency.currency}}</option>
                </select>
            </div>
            <div class="input-container">
                <input type="submit" class="btn" value="Converter"/>
            </div>
             <div class="input-container">
                <label for="result">Result: </label>
                <input type="text" name="result" v-model="result"/>
            </div>
        </form>
    </div>
</template>
<script lang="ts">
import { defineComponent} from 'vue'
import MessageSuccess from './MessageSuccess.vue';
import MessageError from './MessageError.vue';

export default defineComponent({
     data() {
        return {
            currencies : [{
                "currency" : "DOLAR",
                "value" : "USD"
            },{
                "currency" : "EURO",
                "value" : "EUR"
            },{
                "currency" : "REAL",
                "value" : "BRL"
            },{
                "currency" : "PESOARG",
                "value" : "ARG"
            },{
                "currency" : "COLOMBIA",
                "value" : "COP"
            }],
            msg: "" as string,
            msgerr: "" as string,
            fromconvert : "",
            toconvert : "",
            result:""
        }
    },
    methods:{
        async getConvertedValue(e:any) {
            e.preventDefault();
            const sameValue = this.fromconvert == this.toconvert ? null : "OK";
            const notSet = this.fromconvert == "" || this.toconvert == "" ? null : "OK"
            if(!sameValue || !notSet){
                this.msgerr = "Please, choose a currency, both fields should be filled!!"
                setTimeout(() => this.msgerr = "",3000);
                return;
            }
            const request = await fetch(`https://economia.awesomeapi.com.br/json/last/${this.fromconvert}-${this.toconvert}`);
            const result = await request.json();
            const values:any = Object.values(result)[0];
            this.result = values.high;
            
            this.msg = "Value converted successfully"
            
            setTimeout(() => this.msg = "",3000);

        }
    },
    components: {
        MessageSuccess,
        MessageError
    }
});
</script>
<style scoped>
    #cform {
        max-width: 400px;
        margin: 0 left;

    }
    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid rgb(30, 52, 100);

    }

    input, select {
        padding: 5px 10px;
        width: 300px;
    }

    .btn {
        background-color: rgb(30, 52, 100);
        color: white;
        font-weight: bold;
        border: 2px solid rgb(30, 52, 100);
        padding: 10px;
        font-size: 16px;
        margin: 0;
        cursor: pointer;
        transition: .5s;
    }

        .btn:hover {
        background-color: rgb(48, 81, 153);
        color: white;
        }
</style>