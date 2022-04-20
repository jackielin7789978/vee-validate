<script>
export default {
    props: {
        label: {
            type: [String, Number],
            default: ''
        },
        error: {
            type: String
        },
        modelValue: {
            type: [String, Number],
            default: ''
        }
    }
}
</script>

<template>
    <div class="base-input">
        <label class="input-label"> {{ label }} <span v-if="error" class="errMsg"> {{ error }}</span></label>
        <input class="input" v-bind="$attrs" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)"/>
        
    </div>
</template>

<style lang="scss" scoped>
.base-input {
    width: 100%;
    margin-bottom: 2rem;
}

.input-label {
    margin-bottom: 0.5rem;
    display: block;
    text-align: left;
}

.input {
    width: 100%;
    padding: 0.2rem 0.4rem;
    font-size: 1rem;
}

.errMsg {
    font-size: 0.8rem;
    color: rgb(211, 22, 22);
    line-height: 1rem;
    margin-left: 0.2rem;
}
</style>