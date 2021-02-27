<template>
        <button v-on:click="addDigit">{{ buttonValue }}</button>
</template>

<script>
export default {
    name:'CalcButton',
    model:{
        event: 'click'
    },
    data(){
        return{
            value: this.buttonValue,
        }
    },
    methods: {
        addDigit(){
           this.$emit('click',this.buttonValue);
        }
    },
    props:['buttonValue'],
}
</script>

<style>

</style>