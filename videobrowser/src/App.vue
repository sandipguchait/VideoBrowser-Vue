<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
import SearchBar from './components/searchBar';
import axios from 'axios';
const API_KEY = 'AIzaSyBpveA1l_jJ6wgJ6efTpraZ8JnPdryMCB8';


export default {
    name: 'App',
    components: {
        SearchBar
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
            }).then(Response => {
                console.log(Response)
            }).catch(error => {
                console.log(error)
            })
        }
    }
}
</script>

<style>
</style>
