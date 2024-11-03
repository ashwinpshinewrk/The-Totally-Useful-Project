<script>
    import { browser } from "$app/environment";

    // Array of wisdom sentences
    let arr = [
        "Get a Job",
        "Oh, you studied how many years? Nice. But employers still want 5 years of experience for that entry-level job. Good luck cracking that stone, buddy.",
        "I sit around doing nothing all day and nobody cares. You try it, though, and they call it 'lack of ambition.' Funny world, huh?",
        "It's not about what you know or even who you know. It's more like… who your dad knows. Did you study that one?",
        "I am literally a rock, but I've had more callbacks than you. Maybe if you added 'sedimentary' to your LinkedIn skills, you'd get noticed too.",
        "So, you are waiting for a company to notice you. Hate to break it to you, but they might as well be waiting for me to grow feet.",
        "They say hard work pays off, but you work too hard, and they call it 'overqualified.' Too little, and they call it 'underqualified.' Meanwhile, here I am... perfectly unqualified for anything. Maybe you’re overthinking this whole 'work' thing.",
        "You know what's funny? Employers say they want someone 'dynamic,' but they also want someone who'll sit still at a desk for eight hours. I mean, pick a lane, am I right?",
        "You think you are immovable in your career? Try being an actual rock. I still get further than some resumes do in the hiring process.",
        "They say, 'do not be a rock in your career path!' Yeah? Well, I've been sitting here, and no one's fired me yet.",
        "When you finally land an interview, but they ghost you? Welcome to my world, friend. We rocks call that 'a Tuesday.'",
        "Study all you want, but sometimes you've just gotta accept that some doors don't open without a rock-hard punch… or nepotism. You got any family in HR?",
        "Every rejection is 'experience.' Too bad 'experience' doesn't buy you food or rent.",
        "Remember, rejection builds 'character.' But if you ask me, I'd rather be an empty character with a paycheck.",
        "Some companies want candidates to work for free to 'prove themselves.' Look, the only thing I've done for free is exist. That's where I draw the line."


    ];

    // Function to speak the wisdom
    function speak(text) {
        if (browser) {
            const synth = window.speechSynthesis;
            const utterance = new SpeechSynthesisUtterance(text);
            synth.speak(utterance);
        }
    }

    // State variables
    let displayedWisdom = ""; // Holds the displayed wisdom
    let showWater = false; // Controls the water emoji visibility

    // Function to water Dobby and display random wisdom
    function waterDobby() {
        const randomWisdom = arr[Math.floor(Math.random() * arr.length)];
        displayedWisdom = randomWisdom;
        speak(randomWisdom); // Speak the wisdom

        // Show water emoji effect
        showWater = true;
        setTimeout(() => {
            showWater = false; // Hide water after 2 seconds
        }, 2000);
    }
</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        text-align: center;
        background-color: #f5f5f5;
        font-family: Arial, sans-serif;
    }
    .title {
        font-size: 2rem;
        font-weight: bold;
    }
    .description {
        margin-top: 0.5rem;
        font-size: 1.2rem;
        color: #555;
    }
    .wisdom {
        margin-top: 1rem;
        color: green;
        font-size: 1.1rem;
        font-weight: bold;
    }
    .dobby-image-container {
        position: relative;
        margin-top: 1.5rem;
        width: 450px;
    }
    .dobby-image {
        width: 100%;
        height: auto;
    }
    .water {
        position: absolute;
        top: -30px;
        left: 50%;
        transform: translateX(-50%);
        font-size: 2rem;
        animation: drop 2s ease-out forwards;
        opacity: 1;
    }
    @keyframes drop {
        0% { opacity: 1; transform: translateY(0) scale(1); }
        100% { opacity: 0; transform: translateY(30px) scale(1.5); }
    }
    .button {
        margin-top: 2rem;
        padding: 10px 20px;
        font-size: 1rem;
        color: white;
        background-color: #4caf50;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
    .button:hover {
        background-color: #45a049;
    }
    .displayed-wisdom {
        margin-top: 1rem;
        font-size: 1rem;
        color: #333;
        font-style: italic;
    }
    .back-button {
        position: absolute;
      width: 100px;
      padding: 10px;
      border: 2px solid black;
      border-radius: 25px;
      font-weight: bold;
      cursor: pointer;
      margin-left: 30%;
      transition: background-color 0.3s;
  }

  .back-button:hover {
      background-color: #e0e0e0;
  }
</style>

<div class="container">
    <div class="title">Here lives Dobby</div>
    <div class="description">Dobby is your pet rock. He is pretty much a free dude.</div>
    <div class="wisdom">Water him to gain wisdom</div>
    <div class="dobby-image-container">
        {#if showWater}
            <div class="water">💧💧💧</div>
        {/if}
        <img src="/dobby.png" alt="Dobby the pet rock" class="dobby-image" />
    </div>
    <button class="button" on:click={waterDobby}>Press to water Dobby</button>
    {#if displayedWisdom}
        <div class="displayed-wisdom">{displayedWisdom}</div>
    {/if}
    <a href="/"><button class="back-button">Back</button></a>
</div>
