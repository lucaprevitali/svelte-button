<script>
  import "./Button.css";
  import { createEventDispatcher } from "svelte";

  export let disabled = false;
  export let tabindex = null;
  export let id = "";
  export let containerClass = "";
  export let primaryColor = "#3182ce";
  export let secondaryColor = "#fff";
  export let variant = "solid";
  export let type = "button";

  const dispatch = createEventDispatcher();

  function onClick(event) {
    event.preventDefault();
    dispatch("change", {
      event,
    });
  }

  $: solidVariant = `
      background-color: ${primaryColor};
      color: ${secondaryColor};
      border-color: ${primaryColor};
    `;

  $: outlineVariant = `
      background-color: ${secondaryColor};
      color: ${primaryColor};
    `;

  $: linkVariant = `
      color: ${primaryColor};
    `;

  let variants = {};

  $: variants = {
    solid: solidVariant,
    outline: outlineVariant,
    link: linkVariant,
  };
</script>

<div class={containerClass}>
  <button
    {id}
    {type}
    class={`svelte-button ${variant}`}
    on:click={disabled ? null : onClick}
    style={variants[variant]}
    {tabindex}
    {disabled}
  >
    <slot />
  </button>
</div>
