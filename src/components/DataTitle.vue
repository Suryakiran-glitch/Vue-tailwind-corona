<template>
    <div class="text-center">
        <h3 class="text-3xl font-bold">{{title}}</h3>
        <div class="text-2xl mb-8 mt-4">
            {{timeStamp}}
        </div>
    </div>
</template>
<script>
import moment from 'moment'
export default {
    name : "DataTitle",
    props : ["title","dataDate"],
    computed: {
        timeStamp : function () {
            return moment(this.dataDate).format('MMMM Do YYYY , h:mm:ss a')
        }
    },
}
</script>
<style>
    
</style>