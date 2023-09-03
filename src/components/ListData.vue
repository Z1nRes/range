<template>

    <datalist class="list" id="list">
        <ListOption v-for="year in years" :year="year" />
    </datalist>
</template>

<script>
import ListOption from './ListOption.vue'

export default {
    components: {
        ListOption,
    },
    props: ['years'],
    data() {
        return {
            
        }
    }
}
</script>

<style>
.list{
    display: flex;
    justify-content: space-between;
    height: auto;
    overflow: hidden;
    margin-top: 16px; 
    width: 100%;
}
</style>