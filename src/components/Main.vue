<template>
    <section id="main-section">

        

        <div class="container">
            <div v-if="!isLoading" class="select-wrapping">
                <Select @searchClickMusicGenre="serchMusicType" @searchClickMusicAuthor="sechMusicAuthor"/>
            </div>
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
            musicAuthor: "",
        }
    },
    methods: {
        serchMusicType: function (musicType){
            // stampo l'argomento su una variabile
            this.musicGenre = musicType
        },
        sechMusicAuthor: function(musicAuthor){
            // stampo l'argomento su una variabile
            this.musicAuthor = musicAuthor
        },
        filteredArray: function(){
            if ((this.musicGenre === '') && (this.musicAuthor === '')){
                return this.discoArray
            }

            // creo un constante dove verrà salvato una copia dell'array (discoArray), ma filtrato.
            let newDiscoArray = this.discoArray;

            if (this.musicGenre !== '') {
                newDiscoArray = newDiscoArray.filter((element) => {
                    return element.genre === this.musicGenre
                })
            }
            if (this.musicAuthor !== ''){
                newDiscoArray = newDiscoArray.filter((element) => {
                    return element.author === this.musicAuthor
                })
                
            }
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
    
    .container{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        .select-wrapping{
            padding: 20px;
        }
        .fa-3x{
            font-size: 100px;
        }
    }
}
.select-wrapping{
    width: 100%;
}
</style>