<script lang="ts">
    import type { IntegerConfig } from "drizzle-orm/sqlite-core";
    import "./tailwindImport.css";
  
    interface Props {
      /** What background color to use */
      color: string;
      /** Appointment title */
      title: string;
      /** Appointment description */
      description: string;
      /** The timeSpan of the Appointment */
      timeSpan: {
        start: Date,
        end: Date,
      };
      /** Wether the Appointment is overlapping */
      overlap: false | {
        /** If the Appointment floats on the right */
        right: boolean;
      };
    }
    
    const { color = 'lime', title, description, overlap = false, timeSpan }: Props = $props();

    const timeFormatOptions: Intl.DateTimeFormatOptions  = {
        hour: "2-digit", 
        minute: "2-digit"
    }
    const timeFormat = Intl.DateTimeFormat([], timeFormatOptions)
    function getMinutesBetween(timeSpan: { start: Date; end: Date }): number {
        return (timeSpan.end.getTime() - timeSpan.start.getTime()) / (1000 * 60);
    }
    function getPercentageOfDay(timeSpan: { start: Date; end: Date }): number {
        const minBetween = getMinutesBetween(timeSpan)
        const minInDay = 24*60
        const minPercent = 15/minInDay

        return Math.max(minBetween/minInDay, minPercent)
    }
</script>
<div class="rounded-md p-1 text-sm truncate"
    style:background-color={color}
    style:width={(overlap == false) ? "100%" : "75%"}
    style:height="{getPercentageOfDay(timeSpan)*100}%"
    style:margin={overlap == false ? "" : ((overlap.right)? "0 0 0 25%" : "0 25% 0 0")}
    >
    <p class="font-bold max-h-[60px]">{title}</p>
    <p class="text-sm">{timeFormat.format(timeSpan.start)} - {timeFormat.format(timeSpan.end)}</p>
    <p>{description}</p>
    <p>"{getMinutesBetween(timeSpan)/(60*60)*100}%"</p>
</div>
