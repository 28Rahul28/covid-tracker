<template>
    <div>
        
        <select class="form-select mt-10 block w-full border p-3 rounded" v-model="country" @change="datachanged()">
            <option value="0">Global</option>
            <option v-for="option in options" :value="option.ID" :key="option.ID">
                    {{ option.Country }}
            </option>
        </select>
    </div>
</template>

<script>
export default {
    name:"selector",
    data(){
        return{
        country:0,    
        }
    },
    props:['options','total'],
    methods:
    {
        datachanged(){
            if (this.country == 0){
                console.log("Hello")
                this.$emit('get-country',this.total)
            }
            else{
            const country = this.options.find((item) => item.ID === this.country)
            this.$emit('get-country',country)
            }
        }
    },

}
</script>