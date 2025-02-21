<script lang='ts'>
	import { enhance } from '$app/forms';
	import type { PageServerData } from './$types';

	let { data }: { data: PageServerData } = $props();
</script>

<div class="h-screen flex justify-center items-center text-center"><div class="bg-cyan-300 rounded-lg p-4">
	<h1>Hi, {data.user.username}!</h1>
	<p>Your user ID is {data.user.id}.</p>
	<form method='post' action='?/logout' use:enhance>
		<button class="border border-solid border-black rounded-md p-1">Sign out</button>
	</form>
</div></div>
