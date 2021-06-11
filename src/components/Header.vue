<template>
    <header class="d-flex justify-content-between align-items-center px-3">
        <div>
            <img src="../assets/spotify.png" alt="spotify">
        </div>
        <div>
            <select 
            name="genres"
            v-model="selectedGenre"
            @change="$emit('changedGenre', selectedGenre)">
                <option value="">Seleziona un genere</option>
                <option 
                :value="genre"
                v-for="(genre, index) in genres"
                :key="index"
                
                >{{ genre }}</option>
            </select>
        </div>
        
    </header>
        
</template>

        

<script>


export default {
    name: "Header",
    props: {
        "genres": Array
    },
    data: function () {
        return {
            selectedGenre: ""
        }
    },
    components: {
        
    }
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