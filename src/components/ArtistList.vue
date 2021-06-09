<template>

    <main>
        <div class="container main">
            <div class="row justify-content-center">
                <div
                    class="col-6 col-md-4 col-lg-2 cube"
                    v-for="(artist, index) in artists"
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

    components: {
        Artist
    },
    data: function () {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            artists: [],
        }
    },

    created: function () {
        axios
            .get(this.apiUrl)
            .then(
                (response) => {
                    // console.log(response.data);
                    this.artists = response.data.response;
                }
            )
            .catch();
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
    }

</style>