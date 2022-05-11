<template>
    <section>
        <h2>{{title}}</h2>
        <ul>
            <li v-for="(item) in items" :key="item.id"> <br>
                id: {{item.id}} <br>
                titolo originale: {{item.original_title ? item.original_title : item.original_name }} <br>
                titolo: {{item.title ? item.title : item.name}} <br>
                lingua: {{item.original_language}} <br>
                <!-- <img :src="require('./assets/images/'+item.original_language+'jpg')" alt=""> -->
                voto: {{item.vote_average}} <br>
            </li>
        </ul>
    </section>
</template>

<script>
import state from '../store.js';

export default {
    name: 'MainGrid',
    props: {
        items: Array,
        loader: Boolean,
        title: String
    },
    data(){
        return {

        }
    },
    methods : {
    
    },
    computed: {
        mySearch(){
            return state.search
        }
    }
}


</script>