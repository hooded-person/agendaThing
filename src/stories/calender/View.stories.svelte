<script module>
    import { defineMeta } from '@storybook/addon-svelte-csf';
    import CalendarView from './View.svelte';
    import { fn } from '@storybook/test';
  
    // More on how to set up stories at: https://storybook.js.org/docs/writing-stories
    const { Story } = defineMeta({
      title: 'Calendar/View',
      component: CalendarView,
      tags: ['autodocs'],
      argTypes: {
      },
    });
</script>

<!-- More on writing stories with args: https://storybook.js.org/docs/writing-stories/args -->
<Story name="Simple" args={{}} />
  