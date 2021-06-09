<template>
    
    <div class="artist text-center">
        <img 
        class="img-fluid"
        :src="item.poster"
        :alt="item.title"
        >
        <h3>{{ item.title }}</h3>
        <h4>{{ item.author }}</h4>
        <h5>{{ item.year }}</h5>

    </div>
</template>

<script>
export default {
    name: "Artist",
    props: [ "item" ]
}
</script>

<style lang="scss" scoped>
    @import "../style/variables";
    .artist {
        height: 100%;
        padding: 20px;
        background-color: $bg-side-color;

        img {
            height: 150px;
        }

        h3 {
            font-size: 16px;
            color: $main-text;
            text-transform: uppercase;
            margin: 20px 0;
        }
        h4,
        h5 {
            font-size: 14px;
            color: $side-text;
        }
    }
</style>