<template>
    <section>
        <h2>My Play List</h2>
        <form @submit="addSong">
            <label for ="new-song">
                Add a new Song
                <input type="text" name="new-song" v-model="newSong">
            </label>

            <br>
            <label for="new-artist">
                Add the name of the Artist 
                <input type="text" name="new-artist" v-model="newArtist">
            </label>
            <br>
            <input type="submit" value="Submit">
        </form>
        <ul>
            <Song v-for="song in songs" :key="song.songtitle" :song="song" v-on:delete-song="deleteSong" />

        </ul>
    </section>
</template>

<script>
import Song from "./Song.vue";

export default {
    name: 'Playlist',
    components: {
        Song
    },
    data () {
        return {
            newSong: '',
            newArtist: '',

            songs: [
            {
                songtitle: 'First Song',
                artist: 'First Artist',
                completed: false
            },
             {
                songtitle: 'Second Song',
                artist: 'Second Artist',
                completed: false
            },
             {
                songtitle: 'Third Song',
                artist: 'Third Artist',
                completed: false
            }
            ]
        };
    },
methods: {
    addSong (event) {
        event.preventDefault();
        const newSong = this.newSong;
        const newArtist = this.newArtist;
        this.songs.push({
            songtitle: newSong,
            artist: newArtist
        });
        this.newSong = '';
        this.newArtisht = '';
    },
deleteSong(song) {
      const songIndex = this.songs.indexOf(song);
      this.songs.splice(songIndex, 1);
    }
}
};
</script>