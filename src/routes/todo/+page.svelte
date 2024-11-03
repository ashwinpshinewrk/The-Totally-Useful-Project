<script>
    import TodoList from "$lib/components/TodoList.svelte";
    import SuggestedVideo from "$lib/components/SuggestedVideo.svelte";
</script>
<style>
    /* Center the container on the screen */
    .centered-container {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100dvh; /* Full viewport height */
        background-color: #aebac6; /* Optional: Light background for contrast */
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: auto;
    }
    .back-button {
      width: 100px;
      padding: 10px;
      border: 2px solid black;
      border-radius: 25px;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s;
  }

  .back-button:hover {
      background-color: #e0e0e0;
  }
  .dot {
      width: 15px;
      height: 15px;
      background-color: black;
      border-radius: 50%;
      margin-right: 10px;
  }
</style>

<div class="bg-[#aebac6]">
<a href="/"><button class="back-button">Back</button></a>
</div>
<div class="centered-container">
    
    <TodoList />
    <SuggestedVideo/>
</div>