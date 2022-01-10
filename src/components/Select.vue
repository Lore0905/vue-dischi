// aggiungete una select per filtrare i dischi in base al genere: quando l'utente seleziona un genere dalla lista, 
// vengono visualizzati solamente i dischi con il genere corrispondente.

<template>
    <div class="music-genre-wrapping">
        <select name="music-genre" id="music-genre" v-model="musicType" @click="$emit('searchClick', musicType)">
            <option value="Rock" >Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>
    </div>
</template>

<script>
export default {
    name: "Select",
    data: function (){
        return {
            musicType: '',
        }
    }
}
</script>

<style scoped lang="scss">
.music-genre-wrapping{
    text-align: center;
    #music-genre{
        width: 100px;
        padding: 5px 0;
    }
}

</style>