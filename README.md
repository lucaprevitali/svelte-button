# Svelte Button

A simple button component made in Svelte

Try it in the [Svelte REPL](https://svelte.dev/repl/8c2c1227011049e4bc6c6312abe2748f)

## Installation

**Yarn**

```bash
yarn add -D svelte-button
```

**NPM**

```bash
npm i -D svelte-button
```

## Usage

### Basic

```svelte
<script>
  import Button from "svelte-button";

  function handleChange(e) {
    console.log("Event: ", e);
  }
</script>

<Button
  on:change={handleChange}
>
  Svelte Button
</Button>
```

### Custom Attributes

It is possible to add the following attributes to the button:

- `id`
- `disabled`
- `type`
- `tabindex`

And with the `containerClass` prop is possibile to assign a custom class to the container of the button.

### Custom Template

Between the opening and closing "Button" tag you can insert the custom template that you want.
For example to achieve a template with a left icon you can do as following:

```svelte
<Button on:change={handleChange} variant="outline">
  <img src="path/to/icon.svg" alt="custom icon" />
  Save
</Button>
```

### Styling

With the `variant` property you can choose between 3 different buttons styles:

- Solid (default)
- Outline
- Link

To override the default color scheme there are available `primaryColor` and `secondaryColor` properties.

```svelte
<Button
  id="svelte-btn"
  variant="outline"
  primaryColor="red"
  secondaryColor="yellow"
  on:change={handleChange}
>
  Svelte Button
</Button>

<style>
  :global(#svelte-btn) {
    font-size: 26px;
  }
</style>
```

## Props

All the props are optional.

| Prop name      | Default value |
| :------------- | :------------ |
| disabled       | `false`       |
| id             | `""`          |
| containerClass | `""`          |
| type           | `"button"`    |
| tabindex       | `null`        |
| variant        | `"solid"`     |
| primaryColor   | `""`          |
| secondaryColor | `""`          |

## Events

| Name   | Description                                                |
| :----- | :--------------------------------------------------------- |
| change | Triggered by click on the button. Returns the event object |
