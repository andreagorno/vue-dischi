<template>
    <header>
        <img src="../assets/spotify.png" alt="spotify">
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style lang="scss">
    @import "../style/variables.scss";

    header {
        background-color: $bg-side-color;

        img {
            height: 100px;
            margin: 10px;
        }
    }

</style>