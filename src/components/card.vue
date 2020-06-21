<template>
    <div>
        <h2>{{title}}</h2>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "card",
        props: ['title']
    }
</script>

<style scoped>

</style>
