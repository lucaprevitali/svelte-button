<script>
  import { createEventDispatcher } from "svelte";

  export let disabled = false;
  export let tabindex = null;
  export let id = "";
  export let containerClass = "";
  export let primaryColor = "#3182ce";
  export let secondaryColor = "#fff";
  export let variant = "solid";
  export let type = "button";
  let h;

  const dispatch = createEventDispatcher();

  function onClick(event) {
    event.preventDefault();
    dispatch("change", {
      event,
    });
  }

  function applyVariant(variantName = "solid") {
    switch (variantName) {
      case "solid":
        return solidVariant;

      case "outline":
        return outlineVariant;

      case "link":
        return linkVariant;

      default:
        return solidVariant;
    }
  }

  let rootStyle = "";
  $: rootStyle = `
    text-align: center;
    direction: ltr;
    border-radius: ${h / 6}px;
    user-select: none;
    color: ${secondaryColor};
    font-weight: 600;
    line-height: 1;
    padding: 10px 15px;
    cursor: pointer;
  `;

  $: solidVariant = `
      background-color: ${primaryColor};
      color: ${secondaryColor};
      border-radius: ${h / 4}px;
    `;

  $: outlineVariant = `
      background-color: ${secondaryColor};
      color: ${primaryColor};
      border-radius: ${h / 4}px;
      border: 1px solid ${primaryColor};
    `;

  $: linkVariant = `
      background-color: transparent;
      color: ${primaryColor};
      border: none;
      text-decoration: underline;
    `;
</script>

<div class={containerClass} bind:clientHeight={h}>
  <button
    {id}
    {type}
    class="svelte-button"
    on:click={disabled ? null : onClick}
    style={`${rootStyle} ${applyVariant(variant)}`}
    {tabindex}
    {disabled}
  >
    <slot />
  </button>
</div>

<svelte:head>
  <style>
    .svelte-button:hover {
      filter: brightness(0.85);
    }
  </style>
</svelte:head>
