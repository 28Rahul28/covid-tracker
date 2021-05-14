<template>
    <div class="text-center">
        <div class="text-3xl font-bold">{{text}}</div>
        <div class="text-2xl mt-5">{{timestamp}}</div>
        
    </div>
    
    
</template>

<script>
import moment from 'moment'
export default {
    name:'datatitle',
    props:['text','datadate'],
    computed:{
        timestamp: function(){
            return moment(this.datadate).format('MMMM Do YYYY h:mm:ss a')
        }
    }
}
</script>