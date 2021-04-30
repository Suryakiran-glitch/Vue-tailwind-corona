<template>
    <div class="grid md:grid-col-2 gap-4">
        <!--Box 1 -->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h2 class="text-center text-3xl font-bold text-blue-800 mb-4">Cases</h2>
            <div class="text-2xl mb-4">New :
                <span class="font-bold">{{status.NewConfirmed}}</span>
            </div>
             <div class="text-2xl mb-4">New :
                <span class="font-bold">{{status.TotalConfirmed}}</span>
            </div>
        </div>
        <!--Box 2-->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h2 class="text-center text-3xl font-bold text-blue-800 mb-4">Cases</h2>
            <div class="text-2xl mb-4">New :
                <span class="font-bold">{{status.NewDeaths}}</span>
            </div>
             <div class="text-2xl mb-4">New :
                <span class="font-bold">{{status.TotalDeaths}}</span>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name : 'DataCard',
    props : ["status"]
}
</script>
<style>
    
</style>