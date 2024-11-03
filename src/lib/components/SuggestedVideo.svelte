<script>
    import { onMount } from 'svelte';
    import {generate,count} from 'random-words';
    import {GetListByKeyword,GetSuggestData} from 'youtube-search-api';

    let videos = [];

    async function fetchVideos() {
        // Generate a random search term
        const searchTerm = generate(2);
        try {
            const results = await GetListByKeyword(searchTerm,false,3);
            videos = results.items;
            console.log(videos)
        } catch (error) {
            console.error('Error fetching videos:', error);
        }
    }

    // Fetch videos when the component mounts
    onMount(() => {
        fetchVideos();
    });
</script>

<style>
        .suggested-videos {
        width: 300px; /* Set a fixed width for suggested videos */
        background: #f9f9f9;
        padding: 10px;
        border-radius: 8px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .video-item {
        margin: 10px 0;
    }

    iframe {
        width: 100%;
        height: 200px;
        border: none;
    }

</style>


<div class="suggested-videos">
    <h3 class="font-bold">Suggested Videos</h3>
    <p>Don't get distracted</p>
    {#each videos as video, index}
        <div class="video-item" style="top: {Math.random() * 300}px; left: {Math.random() * 100}%;"> <!-- Random position -->
            <iframe src={`https://www.youtube.com/embed/${video.id}`} allowfullscreen></iframe> <!-- Use video.id -->
        </div>
    {/each}
</div>
