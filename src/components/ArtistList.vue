<template>

    <main>

        

        <div class="container main">
            <div class="row justify-content-center w-100">
                <div
                    class="cube"
                    v-for="(artist, index) in filteredArtists"
                    :key="index">
                        <Artist
                            :item="artist"
                        />
                </div>
                
            </div>
        </div>
    </main>
    
</template>

<script>
import Artist from "./Artist.vue";
import axios from "axios";

export default {
    name: "ArtistList",

    props: {
        selectedGenre: String
    },

    components: {
        Artist,
    },
    data: function () {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            artists: [],
            genres: []
        }
    },

    created: function () {
        axios
            .get(this.apiUrl)
            .then(
                (response) => {
                    // console.log(response.data);
                    this.artists = response.data.response;

                    this.artists.forEach(
                        (element) => {
                            if (!this.genres.includes(element.genre)) {
                                this.genres.push(element.genre);
                            }
                    });

                    this.$emit('genresReady', this.genres);
                }
            )

            .catch();
    },
    computed: {
        filteredArtists: function() {
            if(this.selectedGenre == "") {
                return this.artists;
            }

            return this.artists.filter(
                element => element.genre == this.selectedGenre
            );
        }
    }

}
                            
</script>

<style lang="scss" scoped>
    @import "../style/variables.scss";

    @media screen and (max-width:991px) {
        .main {
           display: block !important ;
        }
    }

    main {
        background-color: $bg-color;
        height: calc(100vh - 120px);
        overflow-y: auto;
        
        .main {
            height: calc(100vh - 120px);
            display: flex;
            justify-content: center;
            align-items: center;
        }
    }
    .cube {
        margin: 10px;
        width: calc(100% / 6);
    }

</style>