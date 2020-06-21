<template>
    <div>
        <p>{{title}}</p>
        <div v-for="value in values" :key="value.value">
            <label>{{value.title}}</label>
            <input type="radio" :value='value.value' :checked="value.value === selectedData" @change="valueChangeHandler">
        </div>
    </div>
</template>

<script>
    export default {
        name: "item",
        props: ['title', 'selectedData', 'values'],
        model: {
            prop: 'selectedData',
            event: 'valueChange'
        },
        methods: {
            valueChangeHandler(e) {
                const value = e.target.value;
                this.$emit('valueChange', value);
            }
        }
    }
</script>

<style scoped>

</style>
