<template>
    <div>
        <h1>Result for {{$route.params.id}}</h1>
        <!-- {{$store.state.albums}} -->
        <div v-if="AlbumDataExit"> 
            <div v-for="(album, index) in albumData" :key="album.title">
                <Card 
                :title="album.collectionCensoredName"
                :image="album.artworkUrl100"
                :artistName="album.artistName"
                :url="album.artistViewUrl"
                :color="picker(index)"
                /> 
            </div> 
        </div> 

        <div v-else>
            <h1>Could Not Find Album</h1>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import Card from '~/components/Card'

export default {
    components: {
        Card
    },
    methods: {
        picker(index) {
            return index % 2 == 0 ? 'pink darken-1' : 'blue lighten-2';
        }
    },
    asyncData({params}) {
        return axios.get(`https://itunes.apple.com/search?term=${params.id}&entity=album`)
            .then((response) =>{
                return {albumData: response.data.results}
            })
    },
    computed: {
        AlbumDataExit() {
            return this.albumData.length > 0
        }
    },
    middleware: 'search'
}
</script>