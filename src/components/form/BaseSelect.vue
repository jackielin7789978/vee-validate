<script>
export default {
    props: {
        label: {
            type: [String, Number],
            default: '',
        },
        options: {
            type: Array,
            required: true,
        },
        error: {
            type: String,
        },
        modelValue: {
            type: [String, Number],
            default: ''
        }
    }
}
</script>

<template>
<div class="base-select">
    <label class="label" v-if="label"> {{ label }}</label>
    <select class="select" :value="modelValue" @change="$emit('update:modelValue', $event.target.value)">
        <option class="base-option" v-for="option in options" :key="option.id" :selected="option.text === modelValue">{{ option.text }}</option>
    </select>
    <span v-if="error" class="errMsg">{{ error }}</span>
</div>

</template>

<style lang="scss" scoped>
.label {
    margin-right: 0.5rem;
}
.select {
    font-size: 1rem;
}
.base-select {
    margin-bottom: 2rem;
}
.errMsg {
    font-size: 0.8rem;
    color: rgb(211, 22, 22);
    line-height: 1rem;
    margin-left: 0.5rem;
}
</style>