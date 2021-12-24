<template>
    <section id="main-section">
        <div class="container">
            <Disco v-for="(item, index) in discoArray" :key="index" :discoObject="item"/>
            
        </div>
    </section>
</template>

<script>
import Disco from "./Disco.vue";
import axios from 'axios';
export default {
    name: "Main",
    components: {
        Disco
    },
    data: function(){
        return{
            discoArray: [],
        
        }
    },
    created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            this.discoArray = response.data.response
        });
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';
#main-section{
    padding-top: 10vh;
    
    
    .container{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
}

</style>