<script module>
    import { defineMeta } from '@storybook/addon-svelte-csf';
    import Appointment from './Appointment.svelte';
    import { fn } from '@storybook/test';
  
    // More on how to set up stories at: https://storybook.js.org/docs/writing-stories
    const { Story } = defineMeta({
      title: 'Calendar/Appointment',
      component: Appointment,
      tags: ['autodocs'],
      argTypes: {
        color: { control: 'color' },
      },
    });

    const timeSpan = {
        start: new Date("2025-02-21T21:01:00"),
        end: new Date("2025-02-21T23:59:00"),
    }
</script>

<!-- More on writing stories with args: https://storybook.js.org/docs/writing-stories/args -->
<Story name="Simple" args={{
    title: 'Button',
    timeSpan: timeSpan,
    description: "Lorem ipsum",
}} />

<Story name="Overlap left"  args={{
    title: 'Button',
    timeSpan: timeSpan,
    description: "Lorem ipsum",
    overlap: {right: false},
}} />
<Story name="Overlap right" args={{
    title: 'Button',
    timeSpan: timeSpan,
    description: "Lorem ipsum",
    overlap: {right: true},
}} />

  