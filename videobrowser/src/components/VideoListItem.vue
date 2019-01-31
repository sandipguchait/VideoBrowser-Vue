<template>
    <li class="list-group-item media ">
        <img class="mr-3" :src="thumbnailUrl"/>
        <div class="media-body">
        <h6 class="mt-0 mb-1">{{ video.snippet.title }}</h6>
        </div>
    </li>
</template>

<script>
export default {
    name:'VideoListItem',
    props: ['video'],
    computed:{
        thumbnailUrl(){
            return this.video.snippet.thumbnails.default.url
        }
    }

}
</script>

<style scoped>
li {
    display: flex;
    cursor:pointer;
}
li:hover {
    background-color: #eee;
}
</style>

