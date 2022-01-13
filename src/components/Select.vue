// aggiungete una select per filtrare i dischi in base al genere: quando l'utente seleziona un genere dalla lista, 
// vengono visualizzati solamente i dischi con il genere corrispondente.

<template>
    <div class="select-wrap">
        <!-- music genre -->
        <div class="music-genre-wrapping">
            <select name="music-genre" id="music-genre" v-model="musicType" @change="$emit('searchClickMusicGenre', musicType)">
                <option value="" >All</option>
                <option value="Rock" >Rock</option>
                <option value="Pop">Pop</option>
                <option value="Jazz">Jazz</option>
                <option value="Metal">Metal</option>
                
            </select>
        </div>
        <!-- author name -->
        <div class="music-author-wrapping">
            <select name="author-name" id="author-name" v-model="musicAuthor" @change="$emit('searchClickMusicAuthor', musicAuthor)">
                <option value="" >All</option>
                <option value="Bon Jovi">Bon Jov</option>
                <option value="Queen">Queen</option>
                <option value="Sting">Sting</option>
                <option value="Steve Gadd Band">Steve Gadd Band</option>
                <option value="Iron Maiden" >Iron Maiden</option>
                <option value="Eric Clapton">Eric Clapton</option>
                <option value="Deep Purple">Deep Purple</option>
                <option value="Metallica">Metallica</option>
                <option value="Dave">Weekl</option>
                <option value="Mickeal Jackson">Micheal Jackson</option>
            </select>
        </div>
    </div>
    
</template>

<script>
export default {
    name: "Select",
    data: function (){
        return {
            musicType: '',
            musicAuthor: ''
        }
    }
}
</script>

<style scoped lang="scss">

.select-wrap{
    display: flex;
    .music-genre-wrapping{
        #music-genre{
            width: 100px;
            padding: 5px 0;
            border-radius: 5px;
            background-color: lightgrey;
            color: black;
            margin: 0px 10px,
        }
    }
    .music-author-wrapping{
        #author-name{
            width: 100px;
            padding: 5px 0;
            border-radius: 5px;
            background-color: lightgrey;
            color: black;
            margin: 0px 10px,
        }
    }
}

</style>