<template>
    <h1 class="currentLabel">Currently Playing: None</h1>
    <button class="pauseButton" v-on:click="ControlButton()">Null</button>
    <ul>
        <button class="songButton" v-for="song in objects" :key="song.name" v-on:click="PlaySong(song.filePath, song.name)">
            {{ song.name + " - " + song.artist}}
        </button>
    </ul>
</template>

<script>

import musicLibrary from "./MusicLibrary.vue"

let currentSong = null;
let currentSongName = null;
let playing = false;

export default {
    name: "MusicList",
    data() {
        return {
            objects: musicLibrary.objects
        }
    },
    methods: {
        PlaySong(songPath, songName)
        {
            if (currentSong) {
                currentSong.pause();
                currentSong.remove();
            }

            var audio = new Audio(songPath);
            audio.play();

            const label = document.querySelector(".currentLabel");
            const controlButton = document.querySelector(".pauseButton");

            label.textContent = "Currently Playing: " + songName;
            controlButton.textContent = "Pause";
            controlButton.style.backgroundColor = "rgb(235, 67, 67)"
            controlButton.style.display = "block";
            playing = true;

            currentSongName = songName
            currentSong = audio;
        },
        ControlButton() {

            const label = document.querySelector(".currentLabel");
            const controlButton = document.querySelector(".pauseButton");

            if (playing) {
                playing = false;
                currentSong.pause();
                controlButton.textContent = "Play";
                label.textContent = "Currently Playing: None";
                controlButton.style.backgroundColor = "rgb(67, 235, 123)"
            }else{
                playing = true;
                currentSong.play();
                controlButton.textContent = "Pause";
                label.textContent = "Currently Playing: " + currentSongName;
                controlButton.style.backgroundColor = "rgb(235, 67, 67)"
            }
        }
    }
}

</script>

<style>

    h1 {
        font-family: "Lobster", Helvetica, Arial;
    }

    ul {
        margin: 1em 0 0 0;
        padding: 0;
    }

    button {
        margin: .2em 0;
        border-radius: 15px;
        background-color: rgb(32, 32, 32);
        color: rgb(24, 240, 121);
    }

    .pauseButton {
        margin: 1em 0 0 0;
        display: none;
        width: auto;
        height: auto;
        text-align: center;
        border: none;
        font-family: "Lobster", Helvetica, Arial;
        font-size: 2em;
        background-color: rgb(235, 67, 67);
        color: white;
        border-radius: 15px;
    }

    .songButton {
        display: block;
        width: 100%;
        height: auto;
        padding-left: .2em;
        text-align: left;
        border: none;
        font-family: "Lobster", Helvetica, Arial;
        font-size: 2em;
    }
</style>