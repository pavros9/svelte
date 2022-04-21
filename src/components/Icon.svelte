<script>
  export let text = "";
  export let name;
  export let isLogo = "no-logo";
  if (isLogo === "yes") {
    isLogo = "logo";
  }
</script>

<span class="icon">
  <span class="icon__image">
    <img src="./svg/logo.svg#{name}" class={isLogo} alt={name} />
  </span>
  {#if text}
    <span class="icon__text">{text}</span>
  {/if}
</span>

<style>
  .no-logo {
    width: 32px;
  }
  .logo {
    width: 48px;
    height: 48px;
    border-radius: 4px;
  }
</style>
