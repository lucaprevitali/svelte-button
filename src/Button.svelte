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

  let rootStyle = "";
  $: rootStyle = `
    text-align: center;
    direction: ltr;
    border-radius: ${h / 6}px;
    user-select: none;
    font-weight: 600;
    padding: 10px 15px;
    cursor: pointer;
  `;

  $: solidVariant = `
      background-color: ${primaryColor};
      color: ${secondaryColor};
      border-radius: ${h / 4}px;
      border-color: ${primaryColor};
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

  let variants = {};

  $: variants = {
    solid: solidVariant,
    outline: outlineVariant,
    link: linkVariant,
  };
</script>

<div class={containerClass} bind:clientHeight={h}>
  <button
    {id}
    {type}
    class={`svelte-button ${variant}`}
    on:click={disabled ? null : onClick}
    style={`${rootStyle} ${variants[variant]}`}
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
