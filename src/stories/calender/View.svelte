<script lang="ts">
    import type { IntegerConfig } from "drizzle-orm/sqlite-core";
    import Appointment from "./Appointment.svelte";
    import "./tailwindImport.css";
    import { date } from "drizzle-orm/mysql-core";
  
    interface Props {
    }
    
    const {  }: Props = $props();

    const timeFormatOptions: Intl.DateTimeFormatOptions  = {
        hour: "2-digit", 
        minute: "2-digit"
    }
    const timeFormat = Intl.DateTimeFormat([], timeFormatOptions)
    function getMinutesBetween(timeSpan: { start: Date; end: Date }): number {
        return (timeSpan.end.getTime() - timeSpan.start.getTime()) / (1000 * 60);
    }
</script>
<div class="h-screen flex">
    <Appointment 
        title="Dev meeting"
        timeSpan={{
            start: new Date(),
            end: new Date(Date.now() + 1000*60*60)
        }}
        description="Meeting with meself"
        overlap={false}
        color="cyan"
    />
</div>