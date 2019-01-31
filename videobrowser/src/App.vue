<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <videoList :videos="videos"></videoList> 
    </div>
</template>

<script>
import SearchBar from './components/searchBar';
import VideoList from './components/VideoList';
import axios from 'axios';
const API_KEY = 'AIzaSyBpveA1l_jJ6wgJ6efTpraZ8JnPdryMCB8';


export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
    },
    data(){
        return{
            videos: []
        }
    },
    methods: {
        onTermChange(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params:{
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            }).catch(error => {
                console.log(error)
            })
        }
    }
}
</script>

<style>
</style>
