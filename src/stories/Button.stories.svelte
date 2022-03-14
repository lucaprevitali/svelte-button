<script>
  import { Meta, Template, Story } from "@storybook/addon-svelte-csf";
  import Button from "../components/Button.svelte";
</script>

<Meta
  title="Example/Button"
  component={Button}
  argTypes={{
    variant: {
      options: ["solid", "outline", "link"],
      control: { type: "select" },
    },
    tabindex: {
      control: { type: "number" },
    },
    primaryColor: {
      control: { type: "color" },
    },
    secondaryColor: {
      control: { type: "color" },
    },
  }}
/>

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
