<script>
  import Button from "./Button.svelte";

  const buttons = [
    { text: "Download Now", link: "/download" },
    { text: "Features", link: "/features" },
    { text: "Specs", link: "/specs" },
    { text: "Learn More", link: "/learn" },
  ];
</script>

<div class="button-group">
  {#each buttons as button}
    <Button text={button.text} link={button.link} />
  {/each}
</div>

<style>
  .button-group {
    display: flex;
    gap: 10px;
    justify-content: center;
    max-width: 1500px;
  }
</style>
