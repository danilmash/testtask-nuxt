<template lang="">
    <input type="checkbox" v-model='model' :value='value' :id='id' />
    <label :for='id'>{{ label }}</label>
</template>
<script setup>
    const props = defineProps({
        modelValue: { type: [Array, Boolean] },
        value: { type: [Boolean] },
        label: { type: String },
        id: { type: String },
    })
    const emit = defineEmits(['update:modelValue'])
    const model = computed({
        get() {
            return props.modelValue
        },
        set(value) {
            emit('update:modelValue', value)
        }
    })

</script>
<style lang="">
    
</style>