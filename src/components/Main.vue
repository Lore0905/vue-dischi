<template>
    <section id="main-section">

        <template v-if="!isLoading">
            <Select @searchClick="serchMusicType"/>
        </template>

        <div class="container">
            
            <template v-if="!isLoading">
                <Disco v-for="(item, index) in filteredArray()" :key="index" :discoObject="item"/>
            </template>
            <template v-else>
                <div class="fa-3x">
                    <i class="fas fa-spinner fa-spin"></i>
                </div>
            </template>
           
        </div>
    </section>
</template>

<script>
import Disco from "./Disco.vue";
import axios from 'axios';
import Select from "./Select.vue";
export default {
    name: "Main",
    components: {
        Disco,
        Select
    },
    data: function(){
        return{
            discoArray: [],
            isLoading: true,
            musicGenre: "",
        
        }
    },
    methods: {
        serchMusicType: function (musicType){
            // stampo l'argomento su una variabile
            this.musicGenre = musicType
        },
        filteredArray: function(){

            if (this.musicGenre === 'All'){
                return this.discoArray
            }

            // creo un constante dove verrà salvato una copia dell'array (discoArray), ma filtrato.
            const newDiscoArray = this.discoArray.filter((element) => {
                return element.genre.toLowerCase().includes(this.musicGenre.toLowerCase())
            });
            console.log(newDiscoArray)

            return newDiscoArray
        }
    },
    created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            this.discoArray = response.data.response;

            this.isLoading = false

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

        .fa-3x{
            font-size: 100px;
        }
    }
}

</style>