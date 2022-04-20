<script>
export default {
    props: {
        text: {
            type: String,
            default: 'Submit'
        }
    }
}
</script>

<template>
    <button class="base-btn">{{ text }}</button>
</template>

<style lang="scss" scoped>
.base-btn {
    font-size: 1rem;
    background: transparent;
    border: 1px solid #d5d5d5;
    border-radius: 3px;
    padding: 0.4rem 1rem;
    color: #444;
    cursor: pointer;

    transition: all 0.3s ease;
    
    &:hover {
        background: #444;
        color: #fff;
        border: 1px solid transparent;
    }
}
</style>