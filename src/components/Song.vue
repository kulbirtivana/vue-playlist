<template>
    <li>
    {{ song.songtitle }} by {{song.artist}}

        <button v-on:click="deleteSong (song)">Delete</button>
    </li>
</template>


<script>
export default {
    name: 'Song',
    props: [
        'song'
    ],
   methods: {
       deleteSong (song){
           this.$emit( 'delete-song', song );
       }
   }
}
</script>

<style>

</style>