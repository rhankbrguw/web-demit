<script>

  export let text;
  export let link;

</script>

<button

  class="button"
  on:click={() => (window.location.href = link)}
  on:mouseenter={(e) => {
    const target = e.target;
    if (target instanceof HTMLButtonElement) {
      target.style.background = "linear-gradient(to right, #ffa800, #ffe100)";
    }
  }}
  on:mouseleave={(e) => {
    const target = e.target;
    if (target instanceof HTMLButtonElement) {
      target.style.background = "linear-gradient(to right, #ff7e00, #ffcf00)";
    }
  }}
>
  {text}

</button>

<style>

  .button {
    font-family: "Press Start 2P", sans-serif;
    font-size: 1rem;
    text-transform: uppercase;
    text-shadow:
      1px 1px 0px #000,
      -1px -1px 0px #000;
    background: linear-gradient(to right, #ff7e00, #ffcf00);
    border: 2px solid #000;
    border-radius: 5px;
    padding: 10px 20px;
    color: white;
    cursor: pointer;
    transition:
      transform 0.2s,
      background-color 0.3s;
  }

  .button:hover {
    transform: scale(1.05);
  }
  
</style>
