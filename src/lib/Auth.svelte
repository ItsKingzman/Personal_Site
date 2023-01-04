<script>
	import { supabase } from '$lib/supabase';
	import { error } from '@sveltejs/kit';

	let loading = false;
	let email;
	let password;
	let confirmPassword;
	let signUpVisible = false;

	const handleLogin = async () => {
		try {
			loading = true;
			console.log(email);
			const { error } = await supabase.auth.signInWithPassword({ email, password });
			if (error) throw error;
			alert('Signed In!');
		} catch (error) {
			console.error(error);
			alert(error.error_description || error.message);
		} finally {
			loading = false;
		}
	};

	const handleSignUp = async () => {
		try {
			loading = true;
			console.log(email);
			const { data, error } = await supabase.auth.signUp({ email, password });
			if (error) throw error;
			console.log('SIGNED UP: ', data);
			alert('Signed Up!');
		} catch (error) {
			console.error(error);
			alert(error.error_description || error.message);
		} finally {
			loading = false;
		}
	};
</script>

<div class="container mx-auto my-6 max-w-lg">
	<h1 class="text-2xl font-bold text-center text-grey-800 md:text-3xl">Log In</h1>
	<p class="text-center mt-2">Please Sign In</p>

	{#if !signUpVisible}
		<form on:submit|preventDefault={handleLogin}>
			<div class="flex flex-col text-sm mb-2">
				<label class="font-bold mb-2 text-center text-grey-800" for="email">Email</label>
				<input
					class="appearance-none text-center shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
					name="email"
					type="email"
					placeholder="Your email"
					bind:value={email}
				/>
			</div>

			<div class="flex flex-col text-sm mb-2">
				<label class="font-bold mb-2 text-center text-grey-800" for="password">Password</label>
				<input
					class="appearance-none text-center shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
					name="password"
					type="password"
					placeholder="Your password"
					bind:value={password}
				/>
			</div>
			<button
				type="submit"
				class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-700 text-white py-2 px-4"
			>
				Log In
			</button>
			<br />
			<br />
			<button
				type="button"
				on:click={() => (signUpVisible = !signUpVisible)}
				class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-700 text-white py-2 px-4"
			>
				Sign Up
			</button>
		</form>
	{:else}
		<form on:submit|preventDefault={handleSignUp}>
			<div class="flex flex-col text-sm mb-2">
				<label class="font-bold mb-2 text-center text-grey-800" for="email">Email</label>
				<input
					class="appearance-none text-center shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
					name="email"
					type="email"
					placeholder="Your email"
					bind:value={email}
				/>
			</div>

			<div class="flex flex-col text-sm mb-2">
				<label class="font-bold mb-2 text-center text-grey-800" for="password">Password</label>
				<input
					class="appearance-none text-center shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
					name="password"
					type="password"
					placeholder="Your password"
					bind:value={password}
				/>
			</div>

			<div class="flex flex-col text-sm mb-2">
				<label class="font-bold mb-2 text-center text-grey-800" for="confirmPassword"
					>Confirm Password</label
				>
				<input
					class="appearance-none text-center shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
					name="confirmPassword"
					type="password"
					placeholder="Confirm Password"
					bind:value={confirmPassword}
				/>
			</div>
			<button
				type="submit"
				class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-700 text-white py-2 px-4"
			>
				Sign Up
			</button>
			<!-- <br />
			<br />
			<button
				type="button"
				on:click={() => (signUpVisible = !signUpVisible)}
				class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-700 text-white py-2 px-4"
			>
				Log In
			</button> -->
		</form>
	{/if}
</div>
