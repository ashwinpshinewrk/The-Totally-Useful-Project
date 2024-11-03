<script>
    import { onMount } from "svelte";
    import song from "$lib/asset/song.mp3"
    let isPlaying = false;
    let audio;

    onMount(() => {
        // Initialize the audio element
        audio = new Audio(song);
    });

    function playPause() {
        if (isPlaying) {
            audio.pause();
        } else {
            audio.play();
        }
        isPlaying = !isPlaying;
    }

    function stop() {
        audio.pause();
        audio.currentTime = 0;
        isPlaying = false;
    }
</script>

<style>
    .player {
        display: flex;
        align-items: center;
        gap: 10px;
        background-color: #f3f3f3;
        padding: 10px;
        border-radius: 8px;
        width: 250px;
    }
    .button {
        cursor: pointer;
        padding: 5px 10px;
        border: none;
        border-radius: 5px;
        color: white;
    }
    .playPause {
        background-color: #4caf50;
    }
    .stop {
        background-color: #e74c3c;
    }
</style>

<div class="player">
    <button on:click={playPause} class="button playPause">
        {isPlaying ? "Pause" : "Play"}
    </button>
    <button on:click={stop} class="button stop">Stop</button>
</div>
