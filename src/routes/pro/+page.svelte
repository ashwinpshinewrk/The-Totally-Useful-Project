<script>
  import { onMount } from "svelte";
  import MusicPlayer from "$lib/components/MusicPlayer.svelte";

  let message = "";

  function handleSleepy() {
      message = "I suggest you watch some YouTube shorts or reels to get back on track.";
  }

  function handleActive() {
      message = "I suggest you watch some YouTube shorts or reels to cool down.";
  }
</script>

<style>
  /* Center the main content */
  .container {
      display: flex;
      flex-direction: column;
      align-items:center;
      justify-content: center;
      height: 100vh;
      background-color: #f7f0f0;
      font-family: Arial, sans-serif;
      text-align: center;
  }

  /* Title styling */
  h1 {
      font-size: 2rem;
      font-weight: bold;
      margin: 0;
      display: flex;
      align-items: center;
  }

  /* Dot icon next to title */
  .dot {
      width: 15px;
      height: 15px;
      background-color: black;
      border-radius: 50%;
      margin-right: 10px;
  }

  /* Link styling */
  .link {
      color: #0056b3;
      font-size: 1rem;
      margin-bottom: 20px;
      text-decoration: underline;
  }

  /* Question text styling */
  .question {
      color: green;
      font-size: 1.2rem;
      margin-bottom: 20px;
  }

  /* Button styling */
  .buttons {
      display: flex;
      gap: 20px;
      margin-bottom: 20px;
  }

  .button {
      width: 100px;
      padding: 10px;
      border: 2px solid black;
      border-radius: 25px;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s;
  }

  .button:hover {
      background-color: #e0e0e0;
  }

  /* Message styling */
  .message {
      font-size: 1rem;
      font-weight: bold;
      margin-top: 20px;
  }

  /* Back button styling */
  .back-button {
      margin-top: auto;
      margin-left : 75;
      padding: 5px 15px;
      border: 2px solid black;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s;
  }

  .back-button:hover {
      background-color: #e0e0e0;
      
      
  }
</style>

<div class="container">
  <!-- Title section -->
  <h1 class="">
      <span class="dot"></span>
      Anti-Procrastinator
  </h1>

  <!-- Subtitle link -->
  <a href="#bottom" class="link">Here is another such companion to help you focused..for sure.</a>

  <!-- Question -->
  <p class="question">How do you feel today?</p>

  <!-- Action buttons -->
  <div class="buttons">
      <div class="button" on:click={handleSleepy}>Sleepy</div>
      <div class="button" on:click={handleActive}>Active</div>
  </div>

  <!-- Displayed message -->
  <p class="message">{message}</p>
  <br>

  <div>
    <p class="font-serif font-medium">Here is some music to help you relaxxx...</p>
    <MusicPlayer />
  </div>

  <!-- Back button -->
</div>
<button class="back-button"><a href="/">Back</a></button>
