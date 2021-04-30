<template>
    <div>
        <select @change="onChange()" v-model="selected" class="form-select  w-full mt-10 p-3 border rounded">
            <option value="0">Select Country</option>
            <option v-for="country in countries" :key="country.ID" :value="country.ID">
                {{country.Country}}
            </option>
        </select>
    </div>
</template>
<script>
export default {
    name : "Country Select",
    props : ["countries"],
    data() {
        return {
            selected : 0
        }
    },
    methods : {
        onChange() {
            const country = this.countries.find(item => item.ID === this.selected)
            this.$emit('get-country' , country)
        }
    }
}
</script>
<style>
    
</style>