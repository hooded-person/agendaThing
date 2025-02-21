<script lang='ts'>
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';

	let { form }: { form: ActionData } = $props();
</script>

<div class="h-screen flex justify-center items-center text-center"><div class="bg-cyan-300 rounded-lg p-4">
	<h1 class="font-bold text-2xl mb-3">Login/Register</h1>
	<form method='post' action='?/login' use:enhance>
		<label>
			Username <br>
			<input class="border border-solid border-cyan-650 rounded-md bg-cyan-200" name='username' />
		</label><br>
		<label>
			Password <br>
			<input class="border border-solid border-black rounded-md bg-cyan-200" type='password' name='password' />
		</label><br>
		<button class="mt-2 border border-solid border-black rounded-md p-1">Login</button>
		<button class="border border-solid border-black rounded-md p-1" formaction='?/register'>Register</button>
	</form>
	<p style='color: red'>{form?.message ?? ''}</p>
</div></div>
