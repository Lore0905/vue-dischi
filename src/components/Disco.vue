<template>
        <!-- single disco -->
        <div class="container-wrap-disco">

            <!-- img disco --> 
            <div class="img-disco">
                <img :src="discoObject.poster" :alt="discoObject.title">
            </div>
            <!-- title disco -->
            <div class="title-disco">
                <h2>{{discoObject.title}}</h2>
            </div>
            <!-- author -->
            <div class="author-disco">
                <span>{{discoObject.author}}</span>
            </div>
            <!-- year -->
            <div class="year-disco">
                <span>{{discoObject.year}}</span>
            </div>

        </div>
</template>

<script>
export default {
    name: "Disco",
    props: ["discoObject"],

}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';


    .container-wrap-disco{
        width: calc(100% / 5) ;
        max-width: 200px;
        min-width: 175px;
        height: 350px;
        background-color: $brand_primary_color;
        padding: 20px;
        margin: 10px 20px;

        .img-disco{

        }
        .title-disco{
            text-align: center;
            color: $white-color-text;
            padding: 20px 0px;
            text-transform: uppercase;
            font-size: 13px;
        }
        .author-disco, .year-disco{
            text-align: center;
            color: $grey-color-text;
        }
    }


</style>