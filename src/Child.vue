<script setup>
    import { ref } from 'vue';

    const props = defineProps({
        msg: String
    });
    
    // emit event to send data from child to parent
    const emit = defineEmits(['response'])

    emit('response', 'hello from child')

</script>

<template>
    <h4>Child Component</h4>
    <h5>{{ msg || 'No props passed yet' }}</h5>
</template>

<style scoped>
    h4 {
        color: #000000;
        background-color: #f0f0f0;
        text-align: center;
        /* border-bottom: 1px solid #ccc; */
        padding-bottom: 10px;
        /* border-top: 1px solid #ccc; */
        padding-top: 10px;
    }
</style>