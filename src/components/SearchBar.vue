<template>
    <div>
        <input type="text" v-model="search" placeholder="cerca per titolo" @keyup.enter="cerca">
        <button @click="cerca">clicca</button>
    </div>
</template>

<script>
// import state from '../store.js';

export default {
    name: 'SearchBar',
    data(){
        return {
            search: '',
        }
    },
    methods : {
        cerca(){
            this.$emit('performSearch', this.search)
            this.search= '';
        }
    },
    computed: {
        // mySearch(){
        //     return state.search
        // }
    }
}


</script>