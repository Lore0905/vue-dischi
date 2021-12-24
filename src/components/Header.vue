<template>
    <header>
        <img src="../assets/spotify-logo-png-7072.png" alt="logo spotify">
    </header>
</template>

<script>
export default {
    name: "Header",
}
</script>

<style scoped lang="scss">
header{
    background-color: grey;
    height: 70px;
    display: flex;
    align-items: center;
    
    img{
        width: 60px;
    }
}

</style>