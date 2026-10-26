<script>
  import ButtonGroup from "./components/ButtonGroup.svelte";
  import Header from "./components/Header.svelte";
  import Features from "./components/Features.svelte";
  import Counter from "./lib/Counter.svelte";
  import Copyright from "./components/Copyright.svelte";
</script>

<link
  href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap"
  rel="stylesheet"
/>

<ButtonGroup />
<br />

<main class="app">
  <Header />
  <hr />

  <Counter />

  <Features />
  <hr class="hr-features" />
</main>

<Copyright />

<style>
  .app {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    width: 100%;
    background: #181212;
    font-family: "Press Start 2P", sans-serif;
    color: white;
    text-align: center;
    padding: 20px;
    overflow: hidden;
    box-sizing: border-box;
  }

  hr {
    width: 90%;
    border: 1.5px solid #444;
    margin: 30px 0;
  }

  .hr-features {
    width: 80%;
  }
</style>
