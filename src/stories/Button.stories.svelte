<script>
  import { Meta, Template, Story } from "@storybook/addon-svelte-csf";
  import Button from "../components/Button.svelte";
</script>

<Meta title="Example/Button" component={Button} />

<Template let:args>
  <Button {...args} on:click={args.onClick}>Button</Button>
</Template>

<Story
  name="Solid"
  args={{
    variant: "solid",
  }}
/>

<Story
  name="Outline"
  args={{
    variant: "outline",
  }}
/>

<Story
  name="Link"
  args={{
    variant: "link",
  }}
/>
