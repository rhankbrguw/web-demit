<script>

  import { onMount } from "svelte";

  let targetDate = new Date("2024-12-31T23:59:59");
  let days = 0,
    hours = 0,
    minutes = 0,
    seconds = 0;
  let countdownText = "";

  function updateCountdown() {
    const now = new Date();
    // @ts-ignore
    const diff = targetDate - now;

    if (diff > 0) {
      days = Math.floor(diff / (1000 * 60 * 60 * 24));
      hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
      seconds = Math.floor((diff % (1000 * 60)) / 1000);
      countdownText = `${days} days to go`;
    } else {
      countdownText = "It's now to play!";
    }
  }

  onMount(() => {
    updateCountdown();
    const interval = setInterval(updateCountdown, 1000);
    return () => clearInterval(interval);
  });

</script>

<main>

  <h1>Countdown Timer</h1>
  <p>{countdownText}</p>

  <div class="countdown">
    {#each [{ value: days, label: "Days", max: 30 }, { value: hours, label: "Hours", max: 24 }, { value: minutes, label: "Minutes", max: 60 }, { value: seconds, label: "Seconds", max: 60 }] as item}
      <div class="circle">
        <div class="value">{String(item.value).padStart(2, "0")}</div>
        <div class="label">{item.label}</div>
        <svg>
          <circle cx="50%" cy="50%" r="40"></circle>
          <circle
            cx="50%"
            cy="50%"
            r="40"
            style="stroke-dashoffset: {251.2 -
              (item.value / item.max) * 251.2};"
          ></circle>
        </svg>
      </div>
    {/each}
  </div>

</main>

<style>

  @import url("https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap");

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 20vh;
    background: none;
    font-family: "Press Start 2P", cursive;
    padding: 5rem;
  }

  h1 {
    font-size: 1.7em;
    color: red;
    margin-bottom: 0.5em;
  }

  p {
    font-size: 1.3em;
    color: #666;
    margin-bottom: 1em;
  }

  .countdown {
    display: flex;
    gap: 3rem;
  }

  .circle {
    position: relative;
    width: 100px;
    height: 100px;
  }

  .value {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.5rem;
    font-weight: bold;
    color: #333;
  }

  .label {
    position: absolute;
    bottom: -1.2rem;
    left: 50%;
    transform: translateX(-50%);
    font-size: 0.9rem;
    color: #666;
  }

  svg {
    width: 100px;
    height: 100px;
    transform: rotate(-90deg);
  }

  circle {
    fill: none;
    stroke: rgba(0, 0, 0, 0.1);
    stroke-width: 8;
    r: 40;
    cx: 50%;
    cy: 50%;
  }

  circle:last-child {
    stroke: #000;
    stroke-dasharray: 251.2;
    stroke-dashoffset: 251.2;
    transition: stroke-dashoffset 0.5s ease;
  }

</style>
