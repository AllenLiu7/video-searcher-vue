<template>
  <input @input="onInput"/>
</template>

<script>
export default {
    name: 'SearchBar',
    methods:{
        onInput(e){this.$emit('termChange', e.target.value)}
    }
}
</script>

<style>

</style>